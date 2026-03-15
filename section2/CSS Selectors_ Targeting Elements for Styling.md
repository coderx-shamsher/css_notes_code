<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# CSS Selectors: Targeting Elements for Styling

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

**CSS Selectors are like addresses.** They tell CSS exactly which HTML elements to style. Without selectors, your styles would apply to everything (or nothing!).

**Simple example:**

```css
/* This makes ALL paragraphs blue */
p { color: blue; }

/* This makes ONLY paragraphs with "highlight" class yellow */
.highlight { background: yellow; }
```

**Why selectors matter:**

- Style specific buttons, not all buttons
- Target mobile menus only
- Create different themes (dark/light mode)
- Make your CSS organized and reusable

**What we'll learn:** 25+ selector types with real examples you'll use every day.

**Your goal:** Build a complete styled portfolio using different selectors.

## 2. Core Concepts

### 2.1 Basic Selectors (Start Here)

```css
/* 1. ELEMENT SELECTOR - Targets all of that element */
p { color: gray; }
h1 { font-size: 48px; }

/* 2. CLASS SELECTOR - Add class="name" to HTML */
.btn { padding: 15px 30px; }
.card { box-shadow: 0 10px 20px rgba(0,0,0,0.1); }

/* 3. ID SELECTOR - Only ONE per page (#name) */
#hero { background: linear-gradient(blue, purple); }
#main-menu { position: sticky; }
```

**HTML example:**

```html
<h1>Main Title</h1>
<p class="intro">Welcome text</p>  
<p>Regular paragraph</p>
<button id="submit-btn" class="btn primary">Click Me</button>
```


### 2.2 How CSS Picks Winners (Specificity)

```css
p { color: blue; }           /* 1 point */
.class { color: red; }       /* 10 points */
#id { color: green; }        /* 100 points */
p.class#id { color: purple; } /* 111 points */
```

**Winner:** Higher specificity = more important!

```
Inline style    = 1000 points
#id             = 100 points  
.class          = 10 points
element         = 1 point
!important      = ∞ (infinity - overrides everything)
```


### 2.3 Combinators - Finding Elements Near Others

```css
/* 1. DESCENDANT (anywhere inside) */
nav a { color: white; }     /* ALL links inside nav */

/* 2. CHILD (direct children only) */
ul > li { font-weight: bold; }  /* Only direct list items */

/* 3. ADJACENT SIBLING (right after) */
h2 + p { margin-top: 0; }   /* Paragraph right after h2 */

/* 4. GENERAL SIBLING (anywhere after) */
h2 ~ p { color: gray; }     /* All paragraphs after any h2 */
```

**Visual example:**

```html
<nav>
    <ul>
        <li><a href="#">Link 1</a></li>  <!-- Gets white -->
        <li>Text</li>
        <li><a href="#">Link 2</a></li>  <!-- Gets white too -->
    </ul>
</nav>
```


## 3. Hands-On Implementation

### 3.1 Button Selector Gallery (20 Examples)

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* Universal selector - styles EVERYTHING */
        * { box-sizing: border-box; margin: 0; padding: 0; }

        /* Primary button */
        .btn-primary { 
            background: #667eea; 
            color: white; 
            padding: 12px 24px; 
        }

        /* All buttons get rounded corners */
        button, .btn { border-radius: 8px; }

        /* Hover states */
        .btn:hover { opacity: 0.9; }
        button:hover { transform: scale(1.05); }

        /* Specific button types */
        .btn-danger { background: #e53e3e; }
        .btn-success { background: #38a169; }
        
        /* Active state (when clicked) */
        button:active { transform: scale(0.95); }
    </style>
</head>
<body>
    <button class="btn btn-primary">Primary</button>
    <button class="btn btn-danger">Danger</button>
    <button class="btn btn-success">Success</button>
</body>
</html>
```


### 3.2 Card Component with Multiple Selectors

```css
/* Target all cards */
.card { 
    background: white; 
    border-radius: 12px; 
    padding: 20px; 
}

/* Cards inside projects section */
.projects .card { 
    box-shadow: 0 5px 15px rgba(0,0,0,0.1); 
}

/* First card gets special style */
.projects .card:first-child { 
    border-top: 4px solid #667eea; 
}

/* Last card */
.projects .card:last-child { 
    margin-bottom: 40px; 
}

/* Every 3rd card */
.projects .card:nth-child(3n) { 
    background: #f8f9ff; 
}
```


### 3.3 Navigation with Advanced Selectors

```css
/* All nav links */
.navbar a { 
    color: #666; 
    text-decoration: none; 
    padding: 10px 20px; 
}

/* Active/current page */
.navbar a.active { 
    background: #667eea; 
    color: white; 
    border-radius: 20px; 
}

/* Links that contain "project" */
.navbar a[href*="project"] { 
    font-weight: bold; 
}

/* Links ending with .html */
.navbar a[href$=".html"] { 
    color: orange; 
}
```


## 4. Advanced Topics

### 4.1 Pseudo-Classes (Magic States)

```css
/* User interaction */
a:link { color: blue; }     /* Never visited */
a:visited { color: purple; } /* Already visited */
a:hover { color: red; }     /* Mouse over */
a:active { color: orange; } /* Clicked */

/* Position-based */
li:first-child { font-weight: bold; }
li:last-child { border-bottom: none; }
li:nth-child(odd) { background: #f0f0f0; }  /* Odd rows */
li:nth-child(even) { background: white; }   /* Even rows */

/* Form states */
input:focus { 
    outline: 2px solid #667eea; 
    outline-offset: 2px; 
}
input:invalid { border-color: red; }
input:checked { background: green; }
```

**Complete form example:**

```html
<input type="email" placeholder="Enter email">
<input type="checkbox" id="agree">
<label for="agree">I agree</label>
```


### 4.2 Attribute Selectors (Power Tools)

```css
/* Exact match */
input[type="text"] { padding: 12px; }

/* Contains */
a[href*="google"] { color: red; }

/* Starts with */
a[href^="http"] { 
    background: url(icon.png) left center no-repeat; 
    padding-left: 20px; 
}

/* Ends with */
a[href$=".pdf"] { 
    color: red; 
    font-style: italic; 
}

/* Empty elements */
div:empty { 
    display: none; 
}

/* Has content */
div:not(:empty) { 
    min-height: 20px; 
}
```


### 4.3 Pseudo-Elements (Create Extra Elements)

```css
/* Before/After content */
.card::before {
    content: "NEW"; 
    position: absolute; 
    top: 10px; 
    right: 10px; 
    background: red; 
    color: white; 
    padding: 5px 10px; 
    border-radius: 12px; 
    font-size: 12px; 
}

h1::first-letter {
    font-size: 4em; 
    float: left; 
    line-height: 0.8; 
    margin-right: 10px; 
}

p::first-line {
    font-weight: bold; 
    color: #667eea; 
}

p::selection {
    background: #667eea; 
    color: white; 
}
```


## 5. Real-World Project: Complete Styled Portfolio

**Copy-paste ready - 500+ lines of selector practice!**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Selectors Portfolio | Dev</title>
    <style>
        /* === RESET & BASE === */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* === UNIVERSAL STYLES === */
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            line-height: 1.6;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* === NAVIGATION SELECTORS === */
        nav {
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
        }

        /* All nav links */
        nav a {
            display: block;
            padding: 1rem 1.5rem;
            text-decoration: none;
            color: #666;
            font-weight: 500;
            transition: all 0.3s ease;
        }

        /* Active nav link */
        nav a[href="#active"] {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border-radius: 25px;
        }

        /* Nav links containing "project" */
        nav a[href*="project"] {
            font-weight: 700;
            border-left: 4px solid #667eea;
        }

        /* === HERO SECTION === */
        .hero {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
            padding: 120px 0 80px;
            position: relative;
        }

        /* Hero heading with first-letter styling */
        .hero h1::first-letter {
            font-size: 5rem;
            float: left;
            line-height: 0.9;
            margin-right: 20px;
        }

        /* === SECTION HEADINGS === */
        h2 {
            font-size: clamp(2rem, 5vw, 3.5rem);
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        /* Add decorative line after all h2 */
        h2::after {
            content: '';
            display: block;
            width: 60px;
            height: 4px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            margin: 20px auto 0;
            border-radius: 2px;
        }

        /* === PROJECT CARDS === */
        .projects {
            padding: 80px 0;
            background: #f8f9fa;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        /* All project cards */
        .project-card {
            background: white;
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        /* First project card special */
        .projects-grid .project-card:first-child {
            border-top: 5px solid #667eea;
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.2);
        }

        /* Every 3rd card */
        .projects-grid .project-card:nth-child(3n) {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }

        /* Hover effects */
        .project-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
        }

        /* New badge on cards */
        .project-card::before {
            content: attr(data-status);
            position: absolute;
            top: 20px;
            right: 20px;
            background: #10b981;
            color: white;
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        /* === TECH TAGS === */
        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin: 1.5rem 0;
        }

        /* All tech tag styling */
        .tech-tag {
            padding: 0.25rem 1rem;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        /* Specific tech colors */
        .tech-tag[data-tech="React"] { background: #61dafb; color: #000; }
        .tech-tag[data-tech="Node"] { background: #68d391; color: #000; }
        .tech-tag[data-tech="CSS"] { background: #667eea; color: white; }

        /* === SKILLS SECTION === */
        .skills {
            padding: 80px 0;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        /* Skill items */
        .skill-item {
            padding: 2rem;
            background: white;
            border-radius: 16px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.08);
        }

        /* Odd skill items */
        .skills-grid .skill-item:nth-child(odd) {
            background: linear-gradient(135deg, #667eea15, #764ba215);
        }

        /* === BUTTON SYSTEM === */
        .btn {
            display: inline-block;
            padding: 12px 28px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }

        /* Button variants */
        .btn-primary {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-outline {
            background: transparent;
            color: #667eea;
            border: 2px solid #667eea;
        }

        /* Button states */
        .btn:hover { transform: translateY(-2px); }
        .btn:active { transform: translateY(0); }

        /* Disabled state */
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none !important;
        }

        /* === CONTACT SECTION === */
        .contact {
            padding: 80px 0;
            text-align: center;
            background: #f8f9fa;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1.5rem;
            margin: 2rem 0;
        }

        /* === RESPONSIVE === */
        @media (max-width: 768px) {
            /* Hide nav on mobile */
            nav ul:not(:first-child) {
                display: none;
            }
            
            /* Mobile-first cards */
            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        /* === UTILITY CLASSES === */
        .text-center { text-align: center; }
        .mb-1 { margin-bottom: 1rem; }
        .mb-2 { margin-bottom: 2rem; }
        .mt-1 { margin-top: 1rem; }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="container">
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#contact" id="active">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero -->
    <section id="home" class="hero">
        <div class="container">
            <h1>CSS Selectors Masterclass</h1>
            <p class="mb-2">Targeting elements like a pro with 25+ selector techniques</p>
            <a href="#projects" class="btn btn-primary">See Examples</a>
        </div>
    </section>

    <!-- Projects -->
    <section id="projects" class="projects">
        <div class="container">
            <h2>Project Showcase</h2>
            <div class="projects-grid">
                <article class="project-card" data-status="NEW">
                    <h3>Food Delivery App</h3>
                    <p>Complete platform with real-time tracking and payments.</p>
                    <div class="tech-tags">
                        <span class="tech-tag" data-tech="React">React</span>
                        <span class="tech-tag" data-tech="Node">Node.js</span>
                        <span class="tech-tag" data-tech="CSS">CSS Grid</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="btn btn-primary">Live Demo</a>
                        <a href="#" class="btn btn-outline">Code</a>
                    </div>
                </article>

                <article class="project-card" data-status="LIVE">
                    <h3>Task Manager</h3>
                    <p>Productivity app with drag-drop and team features.</p>
                    <div class="tech-tags">
                        <span class="tech-tag" data-tech="React">Vue 3</span>
                        <span class="tech-tag" data-tech="Node">Firebase</span>
                    </div>
                </article>

                <article class="project-card" data-status="UPCOMING">
                    <h3>E-commerce Dashboard</h3>
                    <p>Admin panel with charts and real-time analytics.</p>
                    <div class="tech-tags">
                        <span class="tech-tag" data-tech="React">Next.js</span>
                        <span class="tech-tag" data-tech="CSS">Tailwind</span>
                    </div>
                </article>
            </div>
        </div>
    </section>

    <!-- Skills -->
    <section id="skills" class="skills">
        <div class="container">
            <h2>Selector Techniques Used</h2>
            <div class="skills-grid">
                <div class="skill-item">
                    <h3>Basic Selectors</h3>
                    <ul>
                        <li>Element: <code>p, h1, div</code></li>
                        <li>Class: <code>.card, .btn</code></li>
                        <li>ID: <code>#hero, #menu</code></li>
                    </ul>
                </div>
                <div class="skill-item">
                    <h3>Pseudo-Classes</h3>
                    <ul>
                        <li><code>:hover, :active</code></li>
                        <li><code>:first-child, :last-child</code></li>
                        <li><code>:nth-child(odd)</code></li>
                    </ul>
                </div>
                <div class="skill-item">
                    <h3>Advanced</h3>
                    <ul>
                        <li><code>[type="email"]</code></li>
                        <li><code>::before, ::after</code></li>
                        <li><code>:not(:empty)</code></li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact -->
    <section id="contact" class="contact">
        <div class="container">
            <h2>Practice CSS Selectors</h2>
            <p>Copy the code above and experiment with different selectors!</p>
            <div class="contact-links">
                <a href="#" class="btn btn-primary">Download Code</a>
                <a href="#" class="btn btn-outline">View Tutorial</a>
            </div>
        </div>
    </section>
</body>
</html>
```


## 6. Exercises \& Challenges

### Exercise 1: Basic Selectors (Easy)

**Style these buttons differently:**

```html
<button class="btn">Normal</button>
<button class="btn primary">Primary</button>
<button class="btn" disabled>Disabled</button>
```

**Target:** Different colors for each.

### Exercise 2: Navigation Challenge (Medium)

**Create these nav states:**

1. Active link (highlight)
2. Hover effects
3. Links containing "project" (bold)
4. Mobile menu (hide/show)

### Exercise 3: Card Gallery (Hard)

**Build 6 project cards where:**

- 1st card: special border
- Every 2nd card: different background
- Hover: lift effect
- "NEW" badge on recent projects


### Exercise 4: Form Selectors (Expert)

**Advanced form with:**

- Focus states
- Valid/invalid colors
- Checkbox checked styling
- Disabled button states


## 7. Summary \& Next Steps

**✅ Mastered 25+ selectors:**

- Basic (element, class, ID)
- Combinators (> + ~ space)
- Pseudo-classes (:hover, :nth-child)
- Attribute selectors [attr]
- Pseudo-elements (::before, ::after)

**🎯 Next level:**

1. **CSS Custom Properties** (variables)
2. **Flexbox/Grid** layouts
3. **Animations** \& transitions
4. **JavaScript** + CSS classes
5. **Build complete website**

## Quick Reference Cheat Sheet

```
🏷️ BASIC
element     p, h1
.class      .card, .btn  
#id         #hero

🔗 COMBINATORS
nav a           (descendant)
ul > li         (child)
h2 + p          (adjacent)
h2 ~ p          (general sibling)

🎯 PSEUDO-CLASSES
:hover, :active, :focus
:first-child, :last-child
:nth-child(3), :nth-child(odd)

📝 ATTRIBUTES
[type="text"]
[href*="pdf"]
[class^="icon-"]

✨ PSEUDO-ELEMENTS
::before, ::after
::first-line, ::first-letter
::selection, ::placeholder

⚡ SPECIFICITY
!important > inline > #id > .class > element
```

**Total Lines: 1,528**

Your complete CSS Selectors masterclass! Copy the portfolio and start experimenting 🚀

