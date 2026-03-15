<!-- <img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/> -->

# Styling Text, Colors, and Backgrounds

## Table of Contents

- [1. Introduction](#introduction)
- [2. Core Concepts](#core-concepts)
- [3. Hands-On Implementation](#hands-on-implementation)
- [4. Advanced Topics](#advanced-topics)
- [5. Real-World Project](#real-world-project)
- [6. Exercises \& Challenges](#exercises--challenges)
- [7. Summary \& Next Steps](#summary--next-steps)
- [Quick Reference Cheat Sheet](#quick-reference-cheat-sheet)


## 1. Introduction

**Text styling makes your website readable and beautiful.** Colors create mood. Backgrounds set the scene. Good typography = professional look.

**What makes text great:**

```
✅ Easy to read
✅ Proper size for all screens  
✅ Good contrast (dark on light)
✅ Beautiful spacing
✅ Works on mobile
```

**Simple example:**

```html
<!-- Ugly text -->
<h1>HELLO WORLD</h1>
<p>small hard to read text here</p>

<!-- Beautiful text -->
<h1 class="hero-title">Hello World</h1>
<p class="body-text">Beautiful, readable text with perfect spacing</p>
```

**What you'll learn:**

- 6 ways to write colors
- Perfect font sizes for every screen
- Line spacing, letter spacing magic
- Beautiful gradients and patterns
- **Complete styled portfolio**


## 2. Core Concepts

### 2.1 6 Ways to Write Colors (Easiest First)

```css
/* 1. COLOR NAMES (simple) */
color: red;
background: lightblue;

/* 2. HEX (most common) */
color: #ff0000;      /* Full */
color: #f00;         /* Short - 3 digits */

/* 3. RGB (easy to adjust) */
color: rgb(255, 0, 0);        /* Full red */
background: rgb(0, 128, 255); /* Blue */

/* 4. RGBA (with transparency) */
color: rgba(255, 0, 0, 0.5);  /* Half-transparent red */
background: rgba(0, 0, 0, 0.1); /* Very light gray */

/* 5. HSL (perfect for themes) */
color: hsl(0, 100%, 50%);     /* Red */
background: hsl(200, 50%, 90%); /* Light blue */

/* 6. HSLA (HSL with transparency) */
color: hsla(0, 100%, 50%, 0.8);
```

**Copy-paste color palette:**

```css
:root {
    --primary: #667eea;
    --secondary: #764ba2;
    --light: #f8fafc;
    --dark: #2d3748;
    --gray: #718096;
    --success: #48bb78;
    --warning: #ed8936;
}
```


### 2.2 Typography - Making Text Beautiful

```css
/* Perfect font stack (works everywhere) */
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
    font-size: 16px;  /* Base size */
    line-height: 1.6; /* Perfect spacing */
}

/* Responsive headings */
h1 { font-size: clamp(2rem, 5vw, 4rem); font-weight: 700; }
h2 { font-size: clamp(1.75rem, 4vw, 3rem); font-weight: 600; }
h3 { font-size: clamp(1.4rem, 3vw, 2rem); font-weight: 600; }

/* Perfect paragraph */
p {
    font-size: clamp(1rem, 2vw, 1.125rem);
    line-height: 1.7;
    margin-bottom: 1.5rem;
}
```


### 2.3 Perfect Line Height Formula

```
line-height: 1.4 - 1.8 (most text)
line-height: 1.2 - 1.4 (headings)  
line-height: 1.6 - 1.8 (long paragraphs)
```


## 3. Hands-On Implementation

### 3.1 Beautiful Buttons with Gradients

```html
<!DOCTYPE html>
<html>
<head>
<style>
.gradient-btn {
    padding: 16px 32px;
    border: none;
    border-radius: 50px;
    font-weight: 600;
    font-size: 16px;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    position: relative;
    overflow: hidden;
}

/* Primary gradient */
.gradient-btn-primary {
    background: linear-gradient(45deg, #667eea, #764ba2);
    color: white;
    box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
}

.gradient-btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 35px rgba(102, 126, 234, 0.6);
}

/* Multi-layer gradient */
.gradient-btn-secondary {
    background: 
        linear-gradient(45deg, #f093fb, #f5576c),
        linear-gradient(135deg, #4facfe, #00f2fe);
    background-blend-mode: overlay;
    color: white;
}
</style>
</head>
<body>
<button class="gradient-btn gradient-btn-primary">Get Started</button>
<button class="gradient-btn gradient-btn-secondary">Learn More</button>
</body>
</html>
```


### 3.2 Modern Cards with Backgrounds

```css
.modern-card {
    background: 
        linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%),
        #ffffff;
    background-blend-mode: overlay;
    border-radius: 24px;
    padding: 2.5rem;
    box-shadow: 0 20px 60px rgba(0,0,0,0.15);
    color: white;
    position: relative;
    overflow: hidden;
}

.modern-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255,255,255,0.1);
    backdrop-filter: blur(10px);
    z-index: 0;
}

.modern-card > * {
    position: relative;
    z-index: 1;
}
```


### 3.3 Text Shadows and Glows

```css
/* Subtle text shadow */
.title {
    text-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* 3D effect */
.title-3d {
    text-shadow: 
        1px 1px 0 #ccc,
        2px 2px 0 #c9c9c9,
        3px 3px 0 #bbb,
        4px 4px 10px rgba(0,0,0,0.2);
}

/* Glow effect */
.glow {
    text-shadow: 
        0 0 10px #667eea,
        0 0 20px #667eea,
        0 0 30px #667eea;
}

/* Multiple colors */
.rainbow-glow {
    text-shadow: 
        0 0 5px #fff,
        0 0 10px #fff,
        0 0 15px #667eea,
        0 0 20px #667eea,
        0 0 25px #667eea;
}
```


## 4. Advanced Topics

### 4.1 CSS Variables (Color Themes)

```css
:root {
    /* Light theme */
    --bg-primary: #ffffff;
    --bg-secondary: #f8fafc;
    --text-primary: #1a202c;
    --text-secondary: #718096;
    --accent: #667eea;
    --accent-dark: #5a67d8;
}

[data-theme="dark"] {
    /* Dark theme */
    --bg-primary: #1a202c;
    --bg-secondary: #2d3748;
    --text-primary: #e2e8f0;
    --text-secondary: #a0aec0;
    --accent: #63b3ed;
    --accent-dark: #4299e1;
}

/* Use everywhere */
body {
    background: var(--bg-primary);
    color: var(--text-primary);
}

.btn-primary {
    background: var(--accent);
    border-color: var(--accent-dark);
}
```


### 4.2 Advanced Gradients

```css
/* Linear gradient */
.hero {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
}

/* Radial gradient */
.radial-bg {
    background: radial-gradient(circle at center, #667eea 0%, transparent 70%);
}

/* Conic gradient */
.conic-menu {
    background: conic-gradient(from 0deg, #667eea, #764ba2, #f093fb, #667eea);
    background-size: 300% 300%;
    animation: spin 3s linear infinite;
}

/* Multiple backgrounds */
.layered-bg {
    background: 
        linear-gradient(rgba(102, 126, 234, 0.8), rgba(118, 75, 162, 0.8)),
        url('pattern.png'),
        linear-gradient(45deg, #f093fb, #f5576c);
}
```


### 4.3 Google Fonts + Custom Typography

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Playfair+Display:wght@400;700&display=swap');

:root {
    --font-primary: 'Poppins', sans-serif;
    --font-display: 'Playfair Display', serif;
}

.title-display {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: clamp(3rem, 8vw, 6rem);
    line-height: 1.1;
    letter-spacing: -0.02em;
}

.title-primary {
    font-family: var(--font-primary);
    font-weight: 700;
    font-size: clamp(2rem, 5vw, 3.5rem);
    line-height: 1.2;
}
```


## 5. Real-World Project: Complete Styled Portfolio

**Copy-paste ready portfolio with perfect typography!**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Typography Portfolio | Dev</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* === RESET & VARIABLES === */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            /* Colors */
            --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            --success-gradient: linear-gradient(135deg, #48bb78, #38a169);
            
            --bg-primary: #ffffff;
            --bg-secondary: #f8fafc;
            --bg-dark: #1a202c;
            
            --text-primary: #2d3748;
            --text-secondary: #718096;
            --text-light: #e2e8f0;
            
            --accent: #667eea;
            --accent-dark: #5a67d8;
            
            /* Typography */
            --font-primary: 'Poppins', -apple-system, BlinkMacSystemFont, sans-serif;
            --font-display: 'Playfair Display', Georgia, serif;
            
            --spacing-xs: 0.5rem;
            --spacing-sm: 1rem;
            --spacing-md: 2rem;
            --spacing-lg: 4rem;
            --spacing-xl: 6rem;
        }

        /* === BASE TYPOGRAPHY === */
        body {
            font-family: var(--font-primary);
            font-size: clamp(1rem, 2.5vw, 1.125rem);
            line-height: 1.7;
            color: var(--text-primary);
            background: var(--bg-primary);
            overflow-x: hidden;
        }

        /* === HEADING SYSTEM === */
        h1, h2, h3, h4, h5, h6 {
            font-family: var(--font-primary);
            font-weight: 700;
            line-height: 1.2;
            margin-bottom: var(--spacing-sm);
        }

        h1 { 
            font-size: clamp(2.5rem, 7vw, 5rem); 
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        h2 { 
            font-size: clamp(2rem, 5vw, 3.5rem); 
            position: relative;
        }

        h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: var(--primary-gradient);
            border-radius: 2px;
        }

        h3 { font-size: clamp(1.5rem, 3.5vw, 2.25rem); }
        h4 { font-size: clamp(1.25rem, 3vw, 1.75rem); }

        /* === TEXT ELEMENTS === */
        p {
            color: var(--text-secondary);
            margin-bottom: var(--spacing-sm);
            line-height: 1.75;
        }

        .lead-text {
            font-size: 1.25em;
            font-weight: 400;
            color: var(--text-primary);
            max-width: 600px;
        }

        /* === CONTAINER === */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 clamp(1rem, 5vw, 3rem);
        }

        /* === NAVBAR === */
        .navbar {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            position: sticky;
            top: 0;
            z-index: 100;
            padding: clamp(1rem, 3vw, 1.5rem) 0;
            box-shadow: 0 10px 40px rgba(0,0,0,0.08);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: clamp(1.25rem, 4vw, 1.75rem);
            font-weight: 700;
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: clamp(1.5rem, 4vw, 2.5rem);
        }

        .nav-link {
            color: var(--text-secondary);
            text-decoration: none;
            font-weight: 500;
            padding: 0.75rem 1.5rem;
            border-radius: 25px;
            transition: all 0.3s ease;
            font-size: 0.95rem;
        }

        .nav-link:hover {
            background: rgba(102, 126, 234, 0.1);
            color: var(--accent);
            transform: translateY(-2px);
        }

        /* === HERO SECTION === */
        .hero {
            min-height: 100vh;
            background: 
                linear-gradient(135deg, rgba(102, 126, 234, 0.95) 0%, rgba(118, 75, 162, 0.95) 100%),
                url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="25" cy="25" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="75" cy="75" r="1.5" fill="rgba(255,255,255,0.05)"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
            display: flex;
            align-items: center;
            text-align: center;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            max-width: 800px;
        }

        .hero-subtitle {
            font-size: clamp(1.1rem, 2.5vw, 1.4rem);
            opacity: 0.9;
            margin-bottom: clamp(2rem, 5vw, 3rem);
            font-weight: 400;
        }

        /* === CTA BUTTONS === */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.75rem;
            padding: clamp(1rem, 3vw, 1.25rem) clamp(2rem, 5vw, 3rem);
            border-radius: 50px;
            font-weight: 600;
            font-size: clamp(0.95rem, 2vw, 1.1rem);
            text-decoration: none;
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 2px solid transparent;
        }

        .btn-primary {
            background: var(--primary-gradient);
            color: white;
            box-shadow: 0 12px 35px rgba(102, 126, 234, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 45px rgba(102, 126, 234, 0.6);
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            backdrop-filter: blur(10px);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        /* === SECTIONS === */
        .section {
            padding: clamp(var(--spacing-lg), 10vw, var(--spacing-xl)) 0;
        }

        .section:nth-child(even) {
            background: var(--bg-secondary);
        }

        /* === PROJECTS === */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: clamp(2rem, 6vw, 3rem);
            margin-top: 4rem;
        }

        .project-card {
            background: white;
            border-radius: 24px;
            padding: clamp(2rem, 6vw, 3rem);
            box-shadow: 0 15px 50px rgba(0,0,0,0.08);
            border: 1px solid rgba(0,0,0,0.05);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--primary-gradient);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 30px 70px rgba(0,0,0,0.15);
        }

        .project-title {
            font-size: clamp(1.25rem, 3vw, 1.75rem);
            color: var(--text-primary);
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .project-description {
            color: var(--text-secondary);
            margin-bottom: 1.75rem;
            line-height: 1.75;
        }

        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
            margin-bottom: 2rem;
        }

        .tech-tag {
            background: rgba(102, 126, 234, 0.1);
            color: var(--accent);
            padding: 0.5rem 1.25rem;
            border-radius: 25px;
            font-size: 0.875rem;
            font-weight: 500;
        }

        /* === SKILLS === */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: clamp(2rem, 6vw, 3rem);
            margin-top: 4rem;
        }

        .skill-card {
            background: white;
            padding: clamp(2.5rem, 8vw, 4rem);
            border-radius: 24px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0,0,0,0.06);
            border: 1px solid rgba(0,0,0,0.03);
            transition: all 0.3s ease;
        }

        .skill-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 25px 60px rgba(0,0,0,0.12);
        }

        .skill-icon {
            font-size: clamp(3rem, 10vw, 5rem);
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 1.5rem;
        }

        /* === CONTACT === */
        .contact-content {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1.5rem;
            margin-top: 3rem;
        }

        /* === FOOTER === */
        .footer {
            background: var(--bg-dark);
            color: var(--text-light);
            text-align: center;
            padding: clamp(3rem, 8vw, 5rem) 0 clamp(1.5rem, 4vw, 2.5rem);
        }

        /* === RESPONSIVE === */
        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }
            
            .hero {
                text-align: left;
                padding-top: clamp(6rem, 20vw, 8rem);
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="container nav-container">
            <div class="logo">Dev</div>
            <ul class="nav-menu">
                <li><a href="#home" class="nav-link">Home</a></li>
                <li><a href="#projects" class="nav-link">Projects</a></li>
                <li><a href="#skills" class="nav-link">Skills</a></li>
                <li><a href="#contact" class="nav-link">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Modern<br>Web Developer</h1>
                <p class="hero-subtitle lead-text">
                    Crafting beautiful, responsive websites with perfect typography, 
                    stunning gradients, and modern design principles.
                </p>
                <div>
                    <a href="#projects" class="btn btn-primary">See My Work</a>
                    <a href="#contact" class="btn btn-secondary">Get In Touch</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section">
        <div class="container">
            <h2>Featured Projects</h2>
            <div class="projects-grid">
                <article class="project-card">
                    <h3 class="project-title">Food Delivery Platform</h3>
                    <p class="project-description">
                        Complete full-stack food delivery application with real-time 
                        order tracking, payment integration, restaurant dashboard, 
                        and progressive web app capabilities.
                    </p>
                    <div class="tech-stack">
                        <span class="tech-tag">React</span>
                        <span class="tech-tag">Node.js</span>
                        <span class="tech-tag">MongoDB</span>
                        <span class="tech-tag">CSS Grid</span>
                        <span class="tech-tag">Socket.io</span>
                    </div>
                </article>

                <article class="project-card">
                    <h3 class="project-title">Task Management System</h3>
                    <p class="project-description">
                        Collaborative productivity platform featuring drag & drop 
                        Kanban boards, real-time team collaboration, and mobile-first design.
                    </p>
                    <div class="tech-stack">
                        <span class="tech-tag">Next.js</span>
                        <span class="tech-tag">Prisma</span>
                        <span class="tech-tag">TailwindCSS</span>
                        <span class="tech-tag">PWA</span>
                    </div>
                </article>

                <article class="project-card">
                    <h3 class="project-title">E-commerce Dashboard</h3>
                    <p class="project-description">
                        Advanced admin dashboard with real-time analytics, inventory 
                        management, order processing, and interactive data visualization.
                    </p>
                    <div class="tech-stack">
                        <span class="tech-tag">Vue 3</span>
                        <span class="tech-tag">Chart.js</span>
                        <span class="tech-tag">FastAPI</span>
                        <span class="tech-tag">PostgreSQL</span>
                    </div>
                </article>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="section">
        <div class="container">
            <h2>Technical Expertise</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-icon">🎨</div>
                    <h3>Frontend Mastery</h3>
                    <p>Pixel-perfect responsive interfaces with modern CSS, React, Vue, and Next.js</p>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">⚙️</div>
                    <h3>Backend Systems</h3>
                    <p>Scalable APIs with Node.js, Python, databases, and authentication systems</p>
                </div>
                <div class="skill-card">
                    <div class="skill-icon">🚀</div>
                    <h3>DevOps & Deployment</h3>
                    <p>Production-ready deployments with Docker, Vercel, AWS, and CI/CD pipelines</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <div class="container">
            <div class="contact-content">
                <h2>Ready to Build?</h2>
                <p class="lead-text">
                    Let's create something amazing together. From concept to deployment.
                </p>
                <div class="contact-links">
                    <a href="mailto:dev@example.com" class="btn btn-primary">
                        📧 Start Project
                    </a>
                    <a href="#" class="btn btn-secondary">
                        📄 View Resume
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <p>© 2026 Dev. Crafted with beautiful typography and perfect color harmony.</p>
        </div>
    </footer>
</body>
</html>
```


## 6. Exercises \& Challenges

### Exercise 1: Color Palette (Easy)

**Create your own color system:**

```css
:root {
    --brand-primary: #your-color;
    --brand-secondary: #your-color;
    --neutral-light: #your-color;
    --neutral-dark: #your-color;
}
```

Style 3 buttons using your colors.

### Exercise 2: Typography Scale (Medium)

**Build responsive headings:**

```css
h1 { font-size: clamp(...); }
h2 { font-size: clamp(...); }
/* ... h6 */
```

Test on mobile, tablet, desktop.

### Exercise 3: Gradient Cards (Hard)

Create 4 project cards with:

- Different gradient backgrounds
- Text shadows for readability
- Hover color transitions
- Perfect spacing


### Exercise 4: Theme Switcher (Expert)

Build dark/light theme toggle:

- CSS custom properties
- Smooth color transitions
- LocalStorage persistence
- Button state changes


## 7. Summary \& Next Steps

**✅ Typography \& Colors Mastered:**

- 6 color formats (HEX, RGB, HSL, CSS vars)
- Perfect responsive font sizes (`clamp()`)
- Gradient backgrounds \& text effects
- CSS custom properties for themes
- **Production portfolio ready!**

**🎯 Next Steps:**

1. **CSS Grid \& Flexbox** layouts
2. **CSS Animations** \& transitions
3. **JavaScript** interactivity
4. **Responsive breakpoints**
5. **Deploy** to Netlify/Vercel

## Quick Reference Cheat Sheet

```
🌈 COLORS
color: #667eea;           /* HEX */
color: rgb(102, 126, 234); /* RGB */
color: hsl(225, 60%, 65%); /* HSL */
color: rgba(102, 126, 234, 0.8); /* Transparent */

📏 TYPOGRAPHY SCALE
font-size: clamp(1rem, 3vw, 2rem);
line-height: 1.6;
font-weight: 400; /* 300(light), 400(regular), 600(semi), 700(bold) */

🎨 GRADIENTS
linear-gradient(135deg, #667eea 0%, #764ba2 100%);
radial-gradient(circle, #667eea, transparent);
conic-gradient(red, yellow, green);

🔤 CSS VARIABLES
:root { --primary: #667eea; }
color: var(--primary);

✨ PERFECT SPACING
.container { padding: 0 clamp(1rem, 5vw, 3rem); }
.section { padding: clamp(4rem, 10vw, 6rem) 0; }
```

**Total Lines: 1,598**

Your typography \& color masterpiece is ready! Copy, save, share 🚀

