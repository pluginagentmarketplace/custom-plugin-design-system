---
name: frontend-technologies
description: Master modern frontend technologies including HTML, CSS, JavaScript, TypeScript, and frameworks like React, Vue, and Angular. Use this skill when learning web development, building responsive interfaces, or mastering component-based architectures.
---

# Frontend Technologies

## Quick Start

Frontend development encompasses the technologies that run in browsers and create user interfaces.

### Essential Technologies:

```javascript
// HTML - Structure
<div id="app">
  <h1>Welcome to Frontend</h1>
</div>

// CSS - Styling
#app h1 { color: blue; font-size: 2rem; }

// JavaScript - Behavior
document.getElementById('app').addEventListener('click', () => {
  console.log('Interactive!');
});
```

## Core Concepts

### 1. HTML5 Fundamentals
- Semantic elements (`<header>`, `<nav>`, `<main>`, `<footer>`)
- Form controls and validation
- Canvas and SVG
- Accessibility attributes (ARIA)
- Meta tags and SEO

### 2. CSS Mastery
- Box model and layout
- Flexbox for one-dimensional layouts
- CSS Grid for two-dimensional layouts
- Media queries for responsive design
- Transitions and animations
- CSS variables and custom properties

### 3. JavaScript ES6+
- Arrow functions and spread operator
- Destructuring and template literals
- Promises and async/await
- Classes and prototypes
- Modules and imports

### 4. Modern Frameworks

#### React Ecosystem
```javascript
// Functional Component with Hooks
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

#### Vue.js
```javascript
// Vue 3 Composition API
export default {
  setup() {
    const count = ref(0);
    return { count };
  },
  template: '<button @click="count++">Count: {{ count }}</button>'
}
```

#### Angular
```typescript
@Component({
  selector: 'app-counter',
  template: '<button (click)="increment()">Count: {{ count }}</button>'
})
export class CounterComponent {
  count = 0;
  increment() { this.count++; }
}
```

### 5. TypeScript for Frontend
- Type annotations
- Interfaces and generics
- Decorators for frameworks
- Strict mode configurations

## Advanced Topics

### State Management
- Context API / Composition API
- Redux / Vuex / Akita
- Zustand for lightweight state

### Performance Optimization
- Code splitting and lazy loading
- Image optimization
- Web Vitals (LCP, FID, CLS)
- Tree shaking and bundler optimization

### Testing Frontend
- Unit testing (Jest, Vitest)
- Component testing (React Testing Library)
- E2E testing (Cypress, Playwright)

### Build Tools
- Webpack, Vite, Parcel
- Module resolution
- Hot Module Replacement (HMR)

## Learning Resources

- **Official React Docs**: https://react.dev
- **Vue.js Guide**: https://vuejs.org
- **MDN Web Docs**: https://developer.mozilla.org
- **TypeScript Handbook**: https://www.typescriptlang.org

## Real-World Projects

1. **Building Responsive Websites** - Responsive design with CSS Grid/Flexbox
2. **Single-Page Application** - React app with routing and state management
3. **Component Library** - Reusable component system with TypeScript
4. **Progressive Web App** - Offline capabilities and service workers
5. **Real-time Dashboard** - WebSocket integration for live updates

---

**Use this skill when:**
- Learning React, Vue, or Angular
- Optimizing frontend performance
- Building responsive designs
- Implementing component architecture
- Working with TypeScript on frontend
