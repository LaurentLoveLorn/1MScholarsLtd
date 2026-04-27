# Development Guide

Quick reference for developing MyAppCoach locally.

## Setup

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Open browser to http://localhost:3000
```

## Project Structure

```
components/          # Reusable React components
├── Header.js       # Navigation with mobile menu
└── Footer.js       # Footer with newsletter

app/               # Next.js pages
├── page.js        # Home page
├── about/         # About page
├── opportunities/ # Opportunities listing
├── pricing/       # Pricing plans
├── contact/       # Contact page
├── login/         # Login page
├── signup/        # Signup page
├── dashboard/     # User dashboard
├── cv-builder/    # CV building tool
├── mentorship/    # Mentor directory
├── blog/          # Blog posts
└── become-mentor/ # Mentor application

styles/
└── globals.css    # Global Tailwind styles
```

## Adding a New Page

1. Create folder in `app/`: `app/new-page/`
2. Create file: `app/new-page/page.js`
3. Add component:

```javascript
'use client'

import Header from '@/components/Header'
import Footer from '@/components/Footer'

export default function NewPage() {
  return (
    <div>
      <Header />
      <section className="pt-32 pb-20">
        <div className="container-custom">
          <h1 className="text-4xl font-bold">New Page</h1>
        </div>
      </section>
      <Footer />
    </div>
  )
}
```

4. Update Header.js to add link

## Common Components

### Button Styles
```html
<!-- Primary Button -->
<button className="btn-primary">Click Me</button>

<!-- Secondary Button -->
<button className="btn-secondary">Click Me</button>

<!-- Gold Button -->
<button className="btn-gold">Click Me</button>
```

### Text Styles
```html
<!-- Section Header -->
<h2 className="section-header">Section Title</h2>

<!-- Gradient Text -->
<span className="gradient-text">Colored Text</span>

<!-- Card Shadow -->
<div className="card-shadow">Content</div>
```

### Layout
```html
<!-- Container -->
<div className="container-custom">
  <!-- Max width 80rem, centered, padded -->
</div>

<!-- Grid -->
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
  <!-- Responsive grid -->
</div>
```

## Responsive Design Breakpoints

```
sm: 640px
md: 768px
lg: 1024px
xl: 1280px
2xl: 1536px
```

Usage:
```html
<div className="text-sm md:text-lg lg:text-2xl">
  Responsive text
</div>
```

## Colors

```javascript
// Tailwind Colors
primary: blue-600      // #2563eb
secondary: slate-900   // #1e1b4b
accent: yellow-500     // #eab308
success: green-500     // #22c55e

// Usage
className="bg-blue-600 text-white border-blue-200"
```

## Icons

Using Lucide React:

```javascript
import { Heart, Menu, X, ArrowRight } from 'lucide-react'

<Heart size={24} className="text-red-500" />
<Menu size={24} />
<X size={24} />
<ArrowRight size={24} />
```

## Forms

```javascript
<input
  type="email"
  placeholder="Email"
  className="px-4 py-3 border border-gray-200 rounded-lg focus:border-blue-600 focus:outline-none"
/>

<textarea
  placeholder="Message"
  rows={6}
  className="w-full px-4 py-3 border border-gray-200 rounded-lg resize-none"
></textarea>

<select className="px-4 py-3 border border-gray-200 rounded-lg">
  <option>Option 1</option>
</select>
```

## State Management

Use React hooks:

```javascript
import { useState } from 'react'

export default function Component() {
  const [count, setCount] = useState(0)
  const [data, setData] = useState(null)
  
  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  )
}
```

## Navigation

```javascript
import Link from 'next/link'

<Link href="/about" className="text-blue-600">
  About Us
</Link>
```

## API Routes (Coming Soon)

Create `app/api/opportunities/route.js`:

```javascript
export async function GET(request) {
  return Response.json({
    opportunities: [/* ... */]
  })
}

export async function POST(request) {
  const data = await request.json()
  // Handle POST
  return Response.json({ success: true })
}
```

## Environment Variables

Create `.env.local`:

```
NEXT_PUBLIC_API_URL=http://localhost:3000/api
DATABASE_URL=your_db_url
```

Access in client:
```javascript
const apiUrl = process.env.NEXT_PUBLIC_API_URL
```

Access in server:
```javascript
const dbUrl = process.env.DATABASE_URL
```

## Testing

```bash
# Manual testing steps:
1. npm run dev
2. Visit http://localhost:3000
3. Test all pages
4. Test forms
5. Test mobile responsiveness
```

## Performance Tips

1. ✅ Use `next/image` for images
2. ✅ Lazy load components
3. ✅ Optimize fonts
4. ✅ Remove unused CSS
5. ✅ Cache API responses

## Debugging

```javascript
// Log to console
console.log('Debug:', variable)

// Check in browser DevTools (F12)
// - Console for errors
// - Network for API calls
// - Performance for speed issues
```

## Common Issues

### Changes not showing
- Clear `.next` folder: `rm -rf .next`
- Restart dev server: `npm run dev`

### Styles not applying
- Check class names spelling
- Run Tailwind: Already included
- Hard refresh: Ctrl+Shift+R

### Images not loading
- Check path is correct
- Use `next/image` for optimization
- Check `public/` folder structure

## Next Steps

1. Add authentication (Firebase)
2. Connect to database (Supabase)
3. Build API routes
4. Add payment processing
5. Deploy to Vercel

## Resources

- [Next.js Docs](https://nextjs.org/docs)
- [Tailwind Docs](https://tailwindcss.com/docs)
- [Lucide Icons](https://lucide.dev)
- [MDN Web Docs](https://developer.mozilla.org)

## Need Help?

- Check the README.md
- Review existing page examples
- Test in browser DevTools
- Ask in documentation

Happy coding! 🚀
