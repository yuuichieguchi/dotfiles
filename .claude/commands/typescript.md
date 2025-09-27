Read CLAUDE.md for universal coding rules, then apply the following TypeScript/Next.js specific patterns.

---

## TypeScript/Next.js Specific Rules

### React Patterns
- **TS-R1 (MUST)** Use functional components with hooks, not class components
- **TS-R2 (MUST)** Extract custom hooks for reusable logic
- **TS-R3 (SHOULD)** Use `useCallback` and `useMemo` for performance optimization
- **TS-R4 (MUST)** Handle loading and error states in components

### Next.js Framework
- **TS-N1 (MUST)** Use App Router (not Pages Router) for new features
- **TS-N2 (SHOULD)** Use Server Components by default, Client Components when needed
- **TS-N3 (MUST)** Implement proper SEO with metadata API
- **TS-N4 (SHOULD)** Use Next.js Image component for optimized images

### TypeScript Code Style
- **TS-C1 (SHOULD)** Use branded types for IDs: `type UserId = Brand<string, 'UserId'>`
- **TS-C2 (MUST)** Use `import type { … }` for type-only imports
- **TS-C3 (SHOULD)** Use Zod for runtime validation

### TypeScript Project Structure
```
src/
├── app/             # Next.js App Router
├── components/
│   ├── ui/         # Reusable UI components
│   └── features/   # Feature-specific components
├── hooks/          # Custom React hooks
├── lib/            # Utility libraries
├── types/          # TypeScript definitions
├── utils/          # Helper functions
└── __tests__/
```

### TypeScript Tools
- **Package Manager**: `pnpm` or `npm`
- **Testing**: `jest --watchAll` or `vitest`
- **Linting**: `eslint --fix .`
- **Formatting**: `prettier --write .`
- **Type Checking**: `tsc --noEmit`

### TypeScript Anti-Patterns
- Using `any` type
- Not handling loading/error states
- Mixing Server and Client Component patterns incorrectly
