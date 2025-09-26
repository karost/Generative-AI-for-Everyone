# Next.js 15 + Tailwind CSS v4 + shadcn/ui Project Setup Template

## Overview
This template provides a step-by-step guide to create a modern web application using Next.js 15, Tailwind CSS v4, and shadcn/ui components with all best practices and configurations.

## Prerequisites
- Node.js 18+ installed
- npm or yarn package manager
- Basic knowledge of React and TypeScript

## Step-by-Step Setup Guide

### Step 1: Create Next.js Project
```bash
npx create-next-app@latest my-app --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
cd my-app
```

### Step 2: Install Tailwind CSS v4
```bash
npm install -D tailwindcss@latest @tailwindcss/postcss@latest postcss@latest
```

### Step 3: Configure PostCSS
Create or update `postcss.config.mjs`:
```javascript
export default {
  plugins: {
    '@tailwindcss/postcss': {},
  },
}
```

### Step 4: Configure Tailwind CSS
Update `tailwind.config.ts`:
```typescript
import type { Config } from 'tailwindcss';

export default {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
    './src/components/**/*.{js,ts,jsx,tsx,mdx}',
    './src/app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
} satisfies Config;
```

### Step 5: Configure Global Styles
Update `src/app/globals.css`:
```css
@import "tailwindcss";

@plugin "tailwindcss-animate";

@custom-variant dark (&:is(.dark *));

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --font-sans: var(--font-geist-sans);
  --font-mono: var(--font-geist-mono);
}

:root {
  --background: oklch(1 0 0);
  --foreground: oklch(0.145 0 0);
  --card: oklch(1 0 0);
  --card-foreground: oklch(0.145 0 0);
  --popover: oklch(1 0 0);
  --popover-foreground: oklch(0.145 0 0);
  --primary: oklch(0.205 0 0);
  --primary-foreground: oklch(0.985 0 0);
  --secondary: oklch(0.97 0 0);
  --secondary-foreground: oklch(0.205 0 0);
  --muted: oklch(0.97 0 0);
  --muted-foreground: oklch(0.556 0 0);
  --accent: oklch(0.97 0 0);
  --accent-foreground: oklch(0.205 0 0);
  --destructive: oklch(0.577 0.245 27.325);
  --border: oklch(0.922 0 0);
  --input: oklch(0.922 0 0);
  --ring: oklch(0.708 0 0);
}

.dark {
  --background: oklch(0.145 0 0);
  --foreground: oklch(0.985 0 0);
  --card: oklch(0.205 0 0);
  --card-foreground: oklch(0.985 0 0);
  --popover: oklch(0.205 0 0);
  --popover-foreground: oklch(0.985 0 0);
  --primary: oklch(0.922 0 0);
  --primary-foreground: oklch(0.205 0 0);
  --secondary: oklch(0.269 0 0);
  --secondary-foreground: oklch(0.985 0 0);
  --muted: oklch(0.269 0 0);
  --muted-foreground: oklch(0.708 0 0);
  --accent: oklch(0.269 0 0);
  --accent-foreground: oklch(0.985 0 0);
  --destructive: oklch(0.704 0.191 22.216);
  --border: oklch(1 0 0 / 10%);
  --input: oklch(1 0 0 / 15%);
  --ring: oklch(0.556 0 0);
}

@layer base {
  * {
    @apply border-border;
  }
  body {
    @apply bg-background text-foreground;
  }
}
```

### Step 6: Install shadcn/ui
```bash
npx shadcn@latest init
```

### Step 7: Install Required Dependencies for shadcn/ui
```bash
npm install -D @radix-ui/react-avatar @radix-ui/react-checkbox @radix-ui/react-dialog @radix-ui/react-dropdown-menu @radix-ui/react-popover @radix-ui/react-select @radix-ui/react-separator @radix-ui/react-slot @radix-ui/react-tooltip class-variance-authority clsx tailwind-merge tailwindcss-animate lucide-react
```

### Step 8: Add Essential Components
```bash
npx shadcn@latest add button card badge input alert dialog dropdown-menu select separator tooltip
```

### Step 9: Create Utility Function
Create `src/lib/utils.ts`:
```typescript
import { type ClassValue, clsx } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```

### Step 10: Set Up Theme Provider (Optional but Recommended)
Create `src/providers/theme-provider.tsx`:
```typescript
'use client';

import { createContext, useContext, useEffect, useState } from 'react';

type Theme = 'dark' | 'light';

interface ThemeProviderProps {
  children: React.ReactNode;
}

interface ThemeProviderState {
  theme: Theme;
  toggleTheme: () => void;
}

const ThemeProviderContext = createContext<ThemeProviderState | undefined>(
  undefined
);

export function ThemeProvider({ 
  children 
}: ThemeProviderProps) {
  const [theme, setTheme] = useState<Theme>('light');
  const [isClient, setIsClient] = useState(false);

  // Initialize theme after client-side hydration 
  useEffect(() => {
    setIsClient(true);
    
    // Determine initial theme based on localStorage or system preference
    const storedTheme = localStorage.getItem('theme');
    const systemTheme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
    const initialTheme = storedTheme || systemTheme;
    
    setTheme(initialTheme as Theme);
  }, []);

  useEffect(() => {
    if (!isClient) return;
    
    const root = window.document.documentElement;
    
    if (theme === 'dark') {
      root.classList.add('dark');
    } else {
      root.classList.remove('dark');
    }
    
    // Save theme to localStorage
    localStorage.setItem('theme', theme);
  }, [theme, isClient]);

  const toggleTheme = () => {
    setTheme(prev => prev === 'dark' ? 'light' : 'dark');
  };

  return (
    <ThemeProviderContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeProviderContext.Provider>
  );
}

export const useTheme = () => {
  const context = useContext(ThemeProviderContext);
  if (context === undefined)
    throw new Error('useTheme must be used within a ThemeProvider');
  return context;
};
```

### Step 11: Create Cart Provider (For E-commerce or Shopping Cart Functionality)
Create `src/providers/cart-provider.tsx`:
```typescript
'use client';

import { createContext, useContext, ReactNode, useState, useEffect } from 'react';

type CartItem = {
  id: number;
  name: string;
  price: number;
  quantity: number;
};

type CartContextType = {
  items: CartItem[];
  addToCart: (item: Omit<CartItem, 'quantity'>) => void;
  removeFromCart: (id: number) => void;
  updateQuantity: (id: number, quantity: number) => void;
  clearCart: () => void;
  getTotalItems: () => number;
  getTotalPrice: () => number;
};

const CartContext = createContext<CartContextType | undefined>(undefined);

export function CartProvider({ children }: { children: ReactNode }) {
  const [items, setItems] = useState<CartItem[]>([]);
  const [isClient, setIsClient] = useState(false);

  // Initialize cart from localStorage after client-side hydration
  useEffect(() => {
    setIsClient(true);
    const savedCart = localStorage.getItem('cart');
    if (savedCart) {
      try {
        setItems(JSON.parse(savedCart));
      } catch (e) {
        console.error('Failed to parse cart from localStorage', e);
        setItems([]);
      }
    }
  }, []);

  // Save cart to localStorage whenever items change
  useEffect(() => {
    if (isClient) {
      localStorage.setItem('cart', JSON.stringify(items));
    }
  }, [items, isClient]);

  const addToCart = (item: Omit<CartItem, 'quantity'>) => {
    setItems(prevItems => {
      const existingItem = prevItems.find(i => i.id === item.id);
      if (existingItem) {
        return prevItems.map(i => 
          i.id === item.id ? { ...i, quantity: i.quantity + 1 } : i
        );
      } else {
        return [...prevItems, { ...item, quantity: 1 }];
      }
    });
  };

  const removeFromCart = (id: number) => {
    setItems(prevItems => prevItems.filter(item => item.id !== id));
  };

  const updateQuantity = (id: number, quantity: number) => {
    if (quantity <= 0) {
      removeFromCart(id);
      return;
    }
    
    setItems(prevItems => 
      prevItems.map(item => 
        item.id === id ? { ...item, quantity } : item
      )
    );
  };

  const clearCart = () => {
    setItems([]);
  };

  const getTotalItems = () => {
    return items.reduce((total, item) => total + item.quantity, 0);
  };

  const getTotalPrice = () => {
    return items.reduce((total, item) => total + item.price * item.quantity, 0);
  };

  const value = {
    items,
    addToCart,
    removeFromCart,
    updateQuantity,
    clearCart,
    getTotalItems,
    getTotalPrice,
  };

  return (
    <CartContext.Provider value={value}>
      {children}
    </CartContext.Provider>
  );
}

export function useCart() {
  const context = useContext(CartContext);
  if (context === undefined) {
    throw new Error('useCart must be used within a CartProvider');
  }
  return context;
}
```

### Step 12: Update Root Layout
Update `src/app/layout.tsx`:
```typescript
import type { Metadata } from "next";
import { Geist, Geist_Mono } from "next/font/google";
import "./globals.css";
import { ThemeProvider } from "@/providers/theme-provider";
import { CartProvider } from "@/providers/cart-provider";

const geistSans = Geist({
  variable: "--font-geist-sans",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});

export const metadata: Metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en" suppressHydrationWarning>
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        <ThemeProvider>
          <CartProvider>
            {children}
          </CartProvider>
        </ThemeProvider>
      </body>
    </html>
  );
}
```

### Step 13: Add Missing Components
```bash
npx shadcn@latest add accordion popover tabs alert-dialog
```

### Step 14: Create Example Components Page
Create `src/app/components-demo/page.tsx`:
```typescript
'use client';

import { useState } from 'react';
import { Alert, AlertDescription, AlertTitle } from '@/components/ui/alert';
import { Badge } from '@/components/ui/badge';
import { Button } from '@/components/ui/button';
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from '@/components/ui/card';
import { Input } from '@/components/ui/input';
import { Separator } from '@/components/ui/separator';
import { 
  AlertCircle,
  CheckCircle2,
  Info,
  Terminal,
  Calendar,
  Settings,
  User,
  Mail
} from 'lucide-react';
import { 
  Accordion,
  AccordionContent,
  AccordionItem,
  AccordionTrigger,
} from '@/components/ui/accordion';
import { 
  Popover,
  PopoverContent,
  PopoverTrigger,
} from '@/components/ui/popover';
import { 
  Tabs,
  TabsContent,
  TabsList,
  TabsTrigger,
} from '@/components/ui/tabs';
import { 
  AlertDialog,
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogFooter,
  AlertDialogHeader,
  AlertDialogTitle,
  AlertDialogTrigger,
} from '@/components/ui/alert-dialog';

export default function ComponentShowcase() {
  const [activeTab, setActiveTab] = useState('overview');
  const [popoverOpen, setPopoverOpen] = useState(false);
  const [isAlertOpen, setIsAlertOpen] = useState(true);

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    alert('Form submitted successfully!');
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-background to-secondary/10 p-4 md:p-8">
      <div className="max-w-6xl mx-auto">
        <header className="mb-12 text-center">
          <h1 className="text-4xl md:text-5xl font-bold bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent mb-4">
            Next.js 15 + Tailwind CSS v4 + shadcn/ui
          </h1>
          <p className="text-lg text-muted-foreground max-w-2xl mx-auto">
            Comprehensive showcase of modern web development with the latest technologies
          </p>
        </header>

        {isAlertOpen && (
          <Alert className="mb-8 animate-in fade-in duration-500">
            <CheckCircle2 className="h-4 w-4" />
            <AlertTitle>Success!</AlertTitle>
            <AlertDescription>
              This project is configured with Next.js 15, Tailwind CSS v4, and shadcn/ui components.
            </AlertDescription>
            <Button 
              variant="ghost" 
              size="sm" 
              className="absolute top-4 right-4 h-8 w-8 p-0"
              onClick={() => setIsAlertOpen(false)}
            >
              ×
            </Button>
          </Alert>
        )}

        <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
          {/* Left Column - Basic Components */}
          <div className="space-y-8">
            <Card className="overflow-hidden">
              <CardHeader className="bg-primary/5">
                <CardTitle className="flex items-center gap-2">
                  <Settings className="h-5 w-5" />
                  UI Components
                </CardTitle>
                <CardDescription>Interactive elements with Tailwind styling</CardDescription>
              </CardHeader>
              <CardContent className="pt-6">
                <div className="space-y-4">
                  <div className="flex flex-wrap gap-2">
                    <Badge variant="default">Default</Badge>
                    <Badge variant="secondary">Secondary</Badge>
                    <Badge variant="destructive">Destructive</Badge>
                    <Badge variant="outline">Outline</Badge>
                    <Badge variant="secondary">With Icon <User className="h-3 w-3 ml-1" /></Badge>
                  </div>
                  
                  <div className="pt-4">
                    <h3 className="font-medium mb-2">Buttons</h3>
                    <div className="flex flex-wrap gap-2">
                      <Button>Primary</Button>
                      <Button variant="secondary">Secondary</Button>
                      <Button variant="outline">Outline</Button>
                      <Button variant="ghost">Ghost</Button>
                      <Button variant="link">Link</Button>
                    </div>
                  </div>
                </div>
              </CardContent>
              <Separator />
              <CardFooter className="flex justify-between">
                <Button variant="outline">Cancel</Button>
                <Button>Submit</Button>
              </CardFooter>
            </Card>

            <Card>
              <CardHeader>
                <CardTitle>Form Elements</CardTitle>
                <CardDescription>Modern form inputs with validation</CardDescription>
              </CardHeader>
              <CardContent>
                <form onSubmit={handleSubmit} className="space-y-4">
                  <div>
                    <label htmlFor="name" className="text-sm font-medium">Name</label>
                    <Input id="name" placeholder="Enter your name" className="mt-1" />
                  </div>
                  <div>
                    <label htmlFor="email" className="text-sm font-medium">Email</label>
                    <Input id="email" type="email" placeholder="Enter your email" className="mt-1" />
                  </div>
                  <Button type="submit" className="w-full">Submit Form</Button>
                </form>
              </CardContent>
            </Card>
          </div>

          {/* Middle Column - Interactive Components */}
          <div className="space-y-8">
            <Card>
              <CardHeader>
                <CardTitle>Interactive Elements</CardTitle>
                <CardDescription>Components with state and functionality</CardDescription>
              </CardHeader>
              <CardContent>
                <Tabs value={activeTab} onValueChange={setActiveTab} className="w-full">
                  <TabsList className="grid w-full grid-cols-3">
                    <TabsTrigger value="overview">Overview</TabsTrigger>
                    <TabsTrigger value="details">Details</TabsTrigger>
                    <TabsTrigger value="settings">Settings</TabsTrigger>
                  </TabsList>
                  <TabsContent value="overview" className="space-y-4">
                    <div className="flex items-center gap-3">
                      <Calendar className="h-8 w-8 text-primary" />
                      <div>
                        <h4 className="font-semibold">Current Tab: Overview</h4>
                        <p className="text-sm text-muted-foreground">Tab content changes dynamically</p>
                      </div>
                    </div>
                    <p className="text-sm">
                      This is the overview tab content. It demonstrates how tabs can be used to organize information.
                    </p>
                  </TabsContent>
                  <TabsContent value="details" className="space-y-4">
                    <h4 className="font-semibold">Details Tab</h4>
                    <p className="text-sm">
                      This is the details tab content. You can put any content you want here.
                    </p>
                  </TabsContent>
                  <TabsContent value="settings" className="space-y-4">
                    <h4 className="font-semibold">Settings Tab</h4>
                    <p className="text-sm">
                      This is the settings tab content. Perfect for configuration options.
                    </p>
                  </TabsContent>
                </Tabs>
              </CardContent>
            </Card>

            <Card>
              <CardHeader>
                <CardTitle>Accordion</CardTitle>
                <CardDescription>Collapsible content sections</CardDescription>
              </CardHeader>
              <CardContent>
                <Accordion type="single" collapsible className="w-full">
                  <AccordionItem value="item-1">
                    <AccordionTrigger>How does Tailwind v4 work?</AccordionTrigger>
                    <AccordionContent>
                      Tailwind CSS v4 uses a new PostCSS-based architecture with CSS @import syntax instead of @tailwind directives. It introduces the @theme directive for styling tokens and uses OKLCH color space for better perceptual uniformity.
                    </AccordionContent>
                  </AccordionItem>
                  <AccordionItem value="item-2">
                    <AccordionTrigger>What are the benefits of shadcn/ui?</AccordionTrigger>
                    <AccordionContent>
                      shadcn/ui provides accessible, customizable React components that you can copy directly into your project. It uses Radix UI for accessibility and works seamlessly with Tailwind CSS.
                    </AccordionContent>
                  </AccordionItem>
                  <AccordionItem value="item-3">
                    <AccordionTrigger>Why Next.js 15?</AccordionTrigger>
                    <AccordionContent>
                      Next.js 15 includes enhanced React Server Components support, improved performance, and better developer experience with features like the App Router and built-in TypeScript support.
                    </AccordionContent>
                  </AccordionItem>
                </Accordion>
              </CardContent>
            </Card>
          </div>

          {/* Right Column - Advanced Components */}
          <div className="space-y-8">
            <Card>
              <CardHeader>
                <CardTitle>Popover & Dialog</CardTitle>
                <CardDescription>Contextual content and modals</CardDescription>
              </CardHeader>
              <CardContent className="space-y-6">
                <div className="flex flex-col items-center gap-4">
                  <Popover open={popoverOpen} onOpenChange={setPopoverOpen}>
                    <PopoverTrigger asChild>
                      <Button variant="outline">
                        Open Popover
                      </Button>
                    </PopoverTrigger>
                    <PopoverContent className="w-80">
                      <div className="grid gap-4">
                        <div className="space-y-2">
                          <h4 className="font-medium leading-none">Popover Content</h4>
                          <p className="text-sm text-muted-foreground">
                            This is an example of a popover component. It can contain any content you want.
                          </p>
                        </div>
                        <div className="grid gap-2">
                          <div className="flex items-center justify-between">
                            <span className="text-sm">Option 1</span>
                            <span className="text-sm text-muted-foreground">Enabled</span>
                          </div>
                          <div className="flex items-center justify-between">
                            <span className="text-sm">Option 2</span>
                            <span className="text-sm text-muted-foreground">Disabled</span>
                          </div>
                        </div>
                      </div>
                    </PopoverContent>
                  </Popover>

                  <AlertDialog>
                    <AlertDialogTrigger asChild>
                      <Button variant="destructive">Show Alert Dialog</Button>
                    </AlertDialogTrigger>
                    <AlertDialogContent>
                      <AlertDialogHeader>
                        <AlertDialogTitle>Are you absolutely sure?</AlertDialogTitle>
                        <AlertDialogDescription>
                          This action cannot be undone. This will permanently delete your account and remove your data from our servers.
                        </AlertDialogDescription>
                      </AlertDialogHeader>
                      <AlertDialogFooter>
                        <AlertDialogCancel>Cancel</AlertDialogCancel>
                        <AlertDialogAction>Continue</AlertDialogAction>
                      </AlertDialogFooter>
                    </AlertDialogContent>
                  </AlertDialog>
                </div>
              </CardContent>
            </Card>

            <Card>
              <CardHeader>
                <CardTitle>Alert Variants</CardTitle>
                <CardDescription>Different types of alerts for feedback</CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <Alert>
                  <Info className="h-4 w-4" />
                  <AlertTitle>Heads up!</AlertTitle>
                  <AlertDescription>
                    You can add components to your app using the cli.
                  </AlertDescription>
                </Alert>
                <Alert variant="destructive">
                  <AlertCircle className="h-4 w-4" />
                  <AlertTitle>Error</AlertTitle>
                  <AlertDescription>
                    Your session has expired. Please log in again.
                  </AlertDescription>
                </Alert>
              </CardContent>
            </Card>

            <Card className="bg-gradient-to-br from-primary/10 to-secondary/10 border-0">
              <CardHeader>
                <CardTitle className="flex items-center gap-2">
                  <Terminal className="h-5 w-5" />
                  Tech Stack
                </CardTitle>
              </CardHeader>
              <CardContent className="space-y-2">
                <div className="flex justify-between">
                  <span>Next.js</span>
                  <span className="font-mono text-sm">v15.x</span>
                </div>
                <div className="flex justify-between">
                  <span>Tailwind CSS</span>
                  <span className="font-mono text-sm">v4.x</span>
                </div>
                <div className="flex justify-between">
                  <span>shadcn/ui</span>
                  <span className="font-mono text-sm">v3.x</span>
                </div>
                <div className="flex justify-between">
                  <span>React</span>
                  <span className="font-mono text-sm">v19.x</span>
                </div>
              </CardContent>
            </Card>
          </div>
        </div>

        <footer className="mt-12 text-center text-sm text-muted-foreground">
          <Separator className="my-6" />
          <p>Next.js 15 + Tailwind CSS v4 + shadcn/ui Showcase • Modern Web Development</p>
        </footer>
      </div>
    </div>
  );
}
```

### Step 15: Create Navbar Component (Optional)
If you want navigation, create `src/components/navbar.tsx`:
```typescript
'use client';

import Link from 'next/link';
import { usePathname } from 'next/navigation';
import { Moon, Sun, Menu } from 'lucide-react';
import { Button } from '@/components/ui/button';
import { Sheet, SheetContent, SheetTrigger } from '@/components/ui/sheet';
import { useTheme } from '@/providers/theme-provider';
import { useState } from 'react';

export default function Navbar() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const pathname = usePathname();
  const { theme, toggleTheme } = useTheme();

  const navLinks = [
    { name: 'Home', href: '/' },
    { name: 'Components', href: '/components-demo' },
  ];

  return (
    <header className="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
      <div className="container flex h-16 items-center justify-between">
        {/* Logo */}
        <div className="flex items-center gap-2">
          <Link href="/" className="flex items-center space-x-2">
            <span className="text-xl font-bold">My App</span>
          </Link>
        </div>

        {/* Desktop Navigation */}
        <nav className="hidden md:flex items-center space-x-6 text-sm font-medium">
          {navLinks.map((link) => (
            <Link
              key={link.href}
              href={link.href}
              className={`transition-colors hover:text-foreground/80 ${
                pathname === link.href ? 'text-foreground' : 'text-foreground/60'
              }`}
            >
              {link.name}
            </Link>
          ))}
        </nav>

        {/* Right side buttons */}
        <div className="flex items-center gap-3">
          <Button variant="ghost" size="icon" onClick={toggleTheme}>
            {theme === 'dark' ? (
              <Sun className="h-5 w-5" />
            ) : (
              <Moon className="h-5 w-5" />
            )}
            <span className="sr-only">Toggle theme</span>
          </Button>

          {/* Mobile menu button */}
          <Sheet open={isMenuOpen} onOpenChange={setIsMenuOpen}>
            <SheetTrigger asChild>
              <Button variant="ghost" size="icon" className="md:hidden">
                <Menu className="h-5 w-5" />
                <span className="sr-only">Toggle menu</span>
              </Button>
            </SheetTrigger>
            <SheetContent side="left" className="w-64">
              <div className="flex flex-col space-y-4 mt-8">
                {navLinks.map((link) => (
                  <Link
                    key={link.href}
                    href={link.href}
                    className={`text-lg font-medium ${
                      pathname === link.href ? 'text-primary' : 'text-foreground/60'
                    }`}
                    onClick={() => setIsMenuOpen(false)}
                  >
                    {link.name}
                  </Link>
                ))}
              </div>
            </SheetContent>
          </Sheet>
        </div>
      </div>
    </header>
  );
}
```

### Step 16: Update Home Page (Optional)
Update `src/app/page.tsx` to include the navbar:
```typescript
import Navbar from '@/components/navbar';

export default function Home() {
  return (
    <div className="min-h-screen flex flex-col">
      <Navbar />
      <main className="flex-grow flex items-center justify-center p-4">
        <div className="text-center">
          <h1 className="text-4xl font-bold mb-4">Next.js 15 + Tailwind CSS v4 + shadcn/ui</h1>
          <p className="text-lg text-muted-foreground mb-8">
            Your modern web application is ready to go!
          </p>
          <a 
            href="/components-demo" 
            className="inline-flex items-center justify-center rounded-md bg-primary px-4 py-2 text-sm font-medium text-primary-foreground shadow transition-colors hover:bg-primary/90 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2"
          >
            View Components Demo
          </a>
        </div>
      </main>
    </div>
  );
}
```

### Step 17: Run the Application
```bash
npm run dev
```

## Important Lessons: Handling Hydration Errors

### Critical Issue: Client-Server State Hydration
When implementing providers that use browser-specific APIs like `localStorage`, you may encounter hydration errors because the server renders differently than the client.

### The Problem:
```typescript
// ❌ This causes hydration errors:
const [theme, setTheme] = useState<Theme>(() => {
  if (typeof window !== 'undefined') {
    const storedTheme = localStorage.getItem('theme');
    return storedTheme || 'light';
  }
  return 'light';
});
```

### The Solution: Client-Side Initialization Pattern
```typescript
// ✅ Proper client-side initialization:
const [theme, setTheme] = useState<Theme>('light');
const [isClient, setIsClient] = useState(false);

// Initialize after client-side hydration
useEffect(() => {
  setIsClient(true);
  const storedTheme = localStorage.getItem('theme');
  if (storedTheme) {
    setTheme(storedTheme as Theme);
  }
}, []);

// Only run effect that accesses browser APIs on client
useEffect(() => {
  if (!isClient) return;
  // Browser-specific operations go here
}, [isClient]);
```

### Key Principles:
1. **Server-first initialization**: Always initialize state with a default value for server rendering
2. **Client-side updates only**: Use useEffect to update state with client-specific values after hydration
3. **Guard browser APIs**: Always check if client-side before accessing localStorage, window, etc.
4. **Conditional effects**: Only run effects that use browser APIs after confirming client-side execution
5. **Use suppressHydrationWarning**: When necessary, use the suppressHydrationWarning attribute on HTML tag to handle minor mismatches

This approach prevents hydration mismatch errors that occur when the server-rendered HTML differs from the initial client render.

## Configuration Notes

### Tailwind CSS v4 Key Changes
1. Uses `@import "tailwindcss";` instead of `@tailwind` directives
2. Introduces `@theme` directive for design tokens
3. Uses OKLCH color space for better perceptual uniformity
4. Has a new PostCSS-based architecture instead of Node.js plugin

### shadcn/ui Configuration
- Components are stored in `src/components/ui/`
- Uses Radix UI for accessibility
- Integrates with Tailwind CSS for styling
- Configured via `components.json` file

### Best Practices Implemented
1. TypeScript throughout the application
2. Proper component composition patterns
3. Accessibility considerations
4. Responsive design principles
5. CSS variable-based theming
6. Performance optimizations

## Troubleshooting

### Common Issues:
1. If you get a "command not found" error for shadcn, try:
   ```bash
   npx shadcn-ui@latest init  # older version
   ```
   
2. If Tailwind isn't working, verify:
   - `postcss.config.mjs` has the correct plugin
   - `tailwind.config.ts` content paths are correct
   - `globals.css` imports Tailwind correctly

3. For theme issues, make sure:
   - ThemeProvider is wrapped around your app
   - CSS variables are properly defined in globals.css
   - localStorage is accessed only after client-side initialization

4. For hydration errors (e.g., "Hydration failed" or "Text content does not match server-rendered HTML"):
   - Make sure all Context Providers that access browser APIs (localStorage, window, etc.) are implemented with the client-side initialization pattern
   - Use the useState + useEffect pattern where initial state is set to a default value for server rendering, then updated after client hydration
   - Consider that some errors may be caused by browser extensions adding attributes after page load

5. For component imports failing, verify:
   - Path aliases are configured in `tsconfig.json`
   - Components are properly installed with shadcn CLI

6. If you encounter missing components errors:
   - Make sure all required components are installed using: `npx shadcn@latest add [component-name]`
   - Check that the component files exist in `src/components/ui/`

## Next Steps

1. Add more components as needed using: `npx shadcn@latest add [component-name]`
2. Customize your theme in `src/app/globals.css`
3. Add your own UI components in `src/components/`
4. Implement your specific application features
5. Add testing (Jest, React Testing Library)
6. Set up deployment configuration (Vercel, Netlify, etc.)

This template provides a solid foundation for building modern web applications with the latest technologies and best practices.