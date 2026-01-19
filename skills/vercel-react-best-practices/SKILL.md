---
name: vercel-react-best-practices
description: React and Next.js performance optimization guidelines from Vercel Engineering. This skill should be used when writing, reviewing, or refactoring React/Next.js code to ensure optimal performance patterns. Triggers on tasks involving React components, Next.js pages, data fetching, bundle optimization, or performance improvements.
license: MIT
metadata:
  author: vercel
  version: "1.0.0"
  source: https://github.com/vercel-labs/agent-skills
---

# Vercel React Best Practices

Comprehensive performance optimization guide for React and Next.js applications, maintained by Vercel Engineering. Contains 45 rules across 8 categories, prioritized by impact to guide automated refactoring and code generation.

## When to Apply

Reference these guidelines when:
- Writing new React components or Next.js pages
- Implementing data fetching (client or server-side)
- Reviewing code for performance issues
- Refactoring existing React/Next.js code
- Optimizing bundle size or load times

## Rule Categories by Priority

| Priority | Category | Impact | Prefix |
|----------|----------|--------|--------|
| 1 | Eliminating Waterfalls | CRITICAL | `async-` |
| 2 | Bundle Size Optimization | CRITICAL | `bundle-` |
| 3 | Server-Side Performance | HIGH | `server-` |
| 4 | Client-Side Data Fetching | MEDIUM-HIGH | `client-` |
| 5 | Re-render Optimization | MEDIUM | `rerender-` |
| 6 | Rendering Performance | MEDIUM | `rendering-` |
| 7 | JavaScript Performance | LOW-MEDIUM | `js-` |
| 8 | Advanced Patterns | LOW | `advanced-` |

## Quick Reference

### 1. Eliminating Waterfalls (CRITICAL)

- `async-defer-await` - Move await into branches where actually used
- `async-parallel` - Use Promise.all() for independent operations
- `async-dependencies` - Use better-all for partial dependencies
- `async-api-routes` - Start promises early, await late in API routes
- `async-suspense-boundaries` - Use Suspense to stream content

### 2. Bundle Size Optimization (CRITICAL)

- `bundle-barrel-imports` - Import directly, avoid barrel files
- `bundle-dynamic-imports` - Use next/dynamic for heavy components
- `bundle-defer-third-party` - Load analytics/logging after hydration
- `bundle-conditional` - Load modules only when feature is activated
- `bundle-preload` - Preload on hover/focus for perceived speed

### 3. Server-Side Performance (HIGH)

- `server-cache-react` - Use React.cache() for per-request deduplication
- `server-cache-lru` - Use LRU cache for cross-request caching
- `server-serialization` - Minimize data passed to client components
- `server-parallel-fetching` - Restructure components to parallelize fetches
- `server-after-nonblocking` - Use after() for non-blocking operations

### 4. Client-Side Data Fetching (MEDIUM-HIGH)

- `client-swr-dedup` - Use SWR for automatic request deduplication
- `client-event-listeners` - Deduplicate global event listeners

### 5. Re-render Optimization (MEDIUM)

- `rerender-defer-reads` - Don't subscribe to state only used in callbacks
- `rerender-memo` - Extract expensive work into memoized components
- `rerender-dependencies` - Use primitive dependencies in effects
- `rerender-derived-state` - Subscribe to derived booleans, not raw values
- `rerender-functional-setstate` - Use functional setState for stable callbacks
- `rerender-lazy-state-init` - Pass function to useState for expensive values
- `rerender-transitions` - Use startTransition for non-urgent updates

### 6. Rendering Performance (MEDIUM)

- `rendering-animate-svg-wrapper` - Animate div wrapper, not SVG element
- `rendering-content-visibility` - Use content-visibility for long lists
- `rendering-hoist-jsx` - Extract static JSX outside components
- `rendering-svg-precision` - Reduce SVG coordinate precision
- `rendering-hydration-no-flicker` - Use inline script for client-only data
- `rendering-activity` - Use Activity component for show/hide
- `rendering-conditional-render` - Use ternary, not && for conditionals

### 7. JavaScript Performance (LOW-MEDIUM)

- `js-batch-dom-css` - Group CSS changes via classes or cssText
- `js-index-maps` - Build Map for repeated lookups
- `js-cache-property-access` - Cache object properties in loops
- `js-cache-function-results` - Cache function results in module-level Map
- `js-cache-storage` - Cache localStorage/sessionStorage reads
- `js-combine-iterations` - Combine multiple filter/map into one loop
- `js-length-check-first` - Check array length before expensive comparison
- `js-early-exit` - Return early from functions
- `js-hoist-regexp` - Hoist RegExp creation outside loops
- `js-min-max-loop` - Use loop for min/max instead of sort
- `js-set-map-lookups` - Use Set/Map for O(1) lookups
- `js-tosorted-immutable` - Use toSorted() for immutability

### 8. Advanced Patterns (LOW)

- `advanced-event-handler-refs` - Store event handlers in refs
- `advanced-use-latest` - useLatest for stable callback refs

---

## Detailed Rules

### 1. Eliminating Waterfalls (CRITICAL)

Waterfalls are the #1 performance killer. Each sequential await adds full network latency.

#### 1.1 Defer Await Until Needed

Move `await` operations into the branches where they're actually used.

**Incorrect:**
```typescript
async function handleRequest(userId: string, skipProcessing: boolean) {
  const userData = await fetchUserData(userId)
  if (skipProcessing) {
    return { skipped: true }
  }
  return processUserData(userData)
}
```

**Correct:**
```typescript
async function handleRequest(userId: string, skipProcessing: boolean) {
  if (skipProcessing) {
    return { skipped: true }
  }
  const userData = await fetchUserData(userId)
  return processUserData(userData)
}
```

#### 1.2 Promise.all() for Independent Operations

**Incorrect:**
```typescript
const user = await fetchUser()
const posts = await fetchPosts()
const comments = await fetchComments()
```

**Correct:**
```typescript
const [user, posts, comments] = await Promise.all([
  fetchUser(),
  fetchPosts(),
  fetchComments()
])
```

#### 1.3 Strategic Suspense Boundaries

**Incorrect:**
```tsx
async function Page() {
  const data = await fetchData() // Blocks entire page
  return (
    <div>
      <Sidebar />
      <DataDisplay data={data} />
    </div>
  )
}
```

**Correct:**
```tsx
function Page() {
  return (
    <div>
      <Sidebar />
      <Suspense fallback={<Skeleton />}>
        <DataDisplay />
      </Suspense>
    </div>
  )
}

async function DataDisplay() {
  const data = await fetchData()
  return <div>{data.content}</div>
}
```

---

### 2. Bundle Size Optimization (CRITICAL)

#### 2.1 Avoid Barrel File Imports

**Incorrect:**
```tsx
import { Check, X, Menu } from 'lucide-react'
// Loads 1,583 modules
```

**Correct:**
```tsx
import Check from 'lucide-react/dist/esm/icons/check'
import X from 'lucide-react/dist/esm/icons/x'
import Menu from 'lucide-react/dist/esm/icons/menu'
// Loads only 3 modules
```

**Alternative (Next.js 13.5+):**
```js
// next.config.js
module.exports = {
  experimental: {
    optimizePackageImports: ['lucide-react', '@mui/material']
  }
}
```

#### 2.2 Dynamic Imports for Heavy Components

**Incorrect:**
```tsx
import { MonacoEditor } from './monaco-editor'
```

**Correct:**
```tsx
import dynamic from 'next/dynamic'

const MonacoEditor = dynamic(
  () => import('./monaco-editor').then(m => m.MonacoEditor),
  { ssr: false }
)
```

#### 2.3 Defer Non-Critical Third-Party Libraries

**Correct:**
```tsx
import dynamic from 'next/dynamic'

const Analytics = dynamic(
  () => import('@vercel/analytics/react').then(m => m.Analytics),
  { ssr: false }
)
```

---

### 3. Server-Side Performance (HIGH)

#### 3.1 Per-Request Deduplication with React.cache()

```typescript
import { cache } from 'react'

export const getCurrentUser = cache(async () => {
  const session = await auth()
  if (!session?.user?.id) return null
  return await db.user.findUnique({
    where: { id: session.user.id }
  })
})
```

#### 3.2 Minimize Serialization at RSC Boundaries

**Incorrect:**
```tsx
async function Page() {
  const user = await fetchUser()  // 50 fields
  return <Profile user={user} />
}
```

**Correct:**
```tsx
async function Page() {
  const user = await fetchUser()
  return <Profile name={user.name} />
}
```

#### 3.3 Use after() for Non-Blocking Operations

```tsx
import { after } from 'next/server'

export async function POST(request: Request) {
  await updateDatabase(request)

  after(async () => {
    logUserAction({ userAgent: request.headers.get('user-agent') })
  })

  return Response.json({ status: 'success' })
}
```

---

### 4. Client-Side Data Fetching (MEDIUM-HIGH)

#### 4.1 Use SWR for Automatic Deduplication

**Incorrect:**
```tsx
const [users, setUsers] = useState([])
useEffect(() => {
  fetch('/api/users').then(r => r.json()).then(setUsers)
}, [])
```

**Correct:**
```tsx
import useSWR from 'swr'

const { data: users } = useSWR('/api/users', fetcher)
```

#### 4.2 Use Passive Event Listeners

```typescript
document.addEventListener('touchstart', handleTouch, { passive: true })
document.addEventListener('wheel', handleWheel, { passive: true })
```

---

### 5. Re-render Optimization (MEDIUM)

#### 5.1 Use Functional setState Updates

**Incorrect:**
```tsx
const addItems = useCallback((newItems: Item[]) => {
  setItems([...items, ...newItems])
}, [items])  // Recreated on every items change
```

**Correct:**
```tsx
const addItems = useCallback((newItems: Item[]) => {
  setItems(curr => [...curr, ...newItems])
}, [])  // Stable callback
```

#### 5.2 Use Lazy State Initialization

**Incorrect:**
```tsx
const [settings, setSettings] = useState(
  JSON.parse(localStorage.getItem('settings') || '{}')
)
```

**Correct:**
```tsx
const [settings, setSettings] = useState(() => {
  const stored = localStorage.getItem('settings')
  return stored ? JSON.parse(stored) : {}
})
```

---

### 6. Rendering Performance (MEDIUM)

#### 6.1 CSS content-visibility for Long Lists

```css
.message-item {
  content-visibility: auto;
  contain-intrinsic-size: 0 80px;
}
```

#### 6.2 Use Explicit Conditional Rendering

**Incorrect:**
```tsx
{count && <span className="badge">{count}</span>}
// Renders "0" when count is 0
```

**Correct:**
```tsx
{count > 0 ? <span className="badge">{count}</span> : null}
```

---

### 7. JavaScript Performance (LOW-MEDIUM)

#### 7.1 Build Index Maps for Repeated Lookups

**Incorrect:**
```typescript
return orders.map(order => ({
  ...order,
  user: users.find(u => u.id === order.userId)
}))
```

**Correct:**
```typescript
const userById = new Map(users.map(u => [u.id, u]))
return orders.map(order => ({
  ...order,
  user: userById.get(order.userId)
}))
```

#### 7.2 Use toSorted() for Immutability

**Incorrect:**
```typescript
const sorted = users.sort((a, b) => a.name.localeCompare(b.name))
// Mutates original array
```

**Correct:**
```typescript
const sorted = users.toSorted((a, b) => a.name.localeCompare(b.name))
// Creates new array
```

---

### 8. Advanced Patterns (LOW)

#### 8.1 useLatest for Stable Callback Refs

```typescript
function useLatest<T>(value: T) {
  const ref = useRef(value)
  ref.current = value
  return ref
}

function useStableCallback<T extends (...args: any[]) => any>(callback: T) {
  const callbackRef = useLatest(callback)
  return useCallback((...args: Parameters<T>) => {
    return callbackRef.current(...args)
  }, []) as T
}
```

---

## React Compiler Note

If your project has [React Compiler](https://react.dev/learn/react-compiler) enabled, the compiler automatically optimizes many of these patterns (memoization, hoisting). However, functional setState updates, direct imports, and proper async patterns remain valuable best practices regardless of compiler support.

## References

- [Vercel Engineering Blog](https://vercel.com/blog)
- [React Documentation](https://react.dev)
- [Next.js Documentation](https://nextjs.org/docs)
- [SWR Documentation](https://swr.vercel.app)
- [better-all](https://github.com/shuding/better-all)
