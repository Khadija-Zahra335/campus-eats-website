# 🍔 Campus Eats – HCI Lab 

**Figma-to-Website Conversion using the Figma MCP Server**

Campus Eats is a food ordering website for university students at PUCIT. Students can browse campus cafes, see popular food, and contact the team. The page was designed in Figma and converted into a responsive website using the **Figma MCP Server** with **Claude Code** in VS Code.

---

## 🔗 Links

| Deliverable | Link |
|---|---|
| 🎨 Figma Design | https://www.figma.com/design/qiJyvjgP0ljIIeJB5wdI39/HCI-Lab-6?node-id=15-288 |
| 🌐 Live Website | [https://campus-eats-website.vercel.app/] |
| 💻 GitHub Repository | [https://github.com/Khadija-Zahra335/campus-eats-website] |

---

## 🛠️ Tools Used

- **Figma** – UI design with Auto Layout, components and variables
- **Figma MCP Server** – connects the Figma file to the AI coding agent
- **Claude Code (VS Code extension)** – MCP client used to generate and refine the code
- **HTML5** – semantic page structure
- **Tailwind CSS** – responsive styling
- **Vercel** – hosting and deployment

---

## 📐 Page Structure

The page has 5 regions (the lab requires at least 4):

| Region | Figma Layer Name | HTML Tag |
|---|---|---|
| Navigation bar | `Navbar` | `<header>` + `<nav>` |
| Hero section with call-to-action | `HeroSection` | `<section>` |
| Cafe card grid (6 cards) | `FeaturesSection` / `FeatureCard` | `<section>` + `<article>` |
| Contact form | `ContactSection` / `ContactForm` | `<section>` + `<form>` |
| Footer | `Footer` | `<footer>` |

---

## 🎨 Task 1: Figma Preparation

- **Auto Layout** is used on every section, row, card and form, so there is no absolute positioning.
- **Resizing:** sections use *Fill container* (width) and *Hug contents* (height). Cards use *Fill* with a minimum width of 320px.
- **Wrap:** the `CardGrid` uses Auto Layout Wrap, so cards move to the next line on small screens.
- **Semantic layer names:** `Navbar`, `HeroSection`, `PrimaryButton`, `FeatureCard`, `ContactForm`, `NameField`, `SubmitButton`, etc.
- **Reusable components:** `WebButton` (Primary/Secondary × Default/Hover), `FeatureCard`, `FormField` (Single/Multi line).
- **Icons** are marked for SVG export.

### Design Variables → CSS Custom Properties

| Figma Variable | CSS Variable | Value |
|---|---|---|
| `color/primary` | `--color-primary` | `#FF6B2C` |
| `color/primary-light` | `--color-primary-light` | `#FFF1EA` |
| `color/primary-dark` | `--color-primary-dark` | `#E5531A` |
| `color/text-dark` | `--color-text-dark` | `#1F1F1F` |
| `color/text-grey` | `--color-text-grey` | `#6B6B6B` |
| `color/surface` | `--color-surface` | `#F7F7F7` |
| `spacing/md` | `--spacing-md` | `16px` |
| `spacing/lg` | `--spacing-lg` | `24px` |
| `spacing/section` | `--spacing-section` | `96px` |
| `radius/md` | `--radius-md` | `12px` |
| `radius/lg` | `--radius-lg` | `20px` |

---

## 🔌 Task 2: Figma MCP Server Setup

The remote Figma MCP server (`https://mcp.figma.com/mcp`) was connected in two ways:

**Claude Code** – `.mcp.json` (project root):

    {
      "mcpServers": {
        "figma": {
          "type": "http",
          "url": "https://mcp.figma.com/mcp"
        }
      }
    }

**VS Code** – `.vscode/mcp.json`:

    {
      "servers": {
        "figma": {
          "type": "http",
          "url": "https://mcp.figma.com/mcp"
        }
      }
    }

After connecting, the Figma account was authenticated with the `/mcp` command in Claude Code.

**MCP tools used:**
- `get_variable_defs` – read the design variables and convert them to CSS custom properties
- `get_design_context` – read the layout structure, spacing and layer names
- `get_screenshot` – compare the code output with the design

---

## 📱 Task 3: Responsiveness & Accessibility

### Responsive Breakpoints

| Screen | Width | Card Grid | Hero | Navigation |
|---|---|---|---|---|
| Desktop | 1440px | 3 columns | Text and image side by side | Full links |
| Tablet | 768px | 2 columns | Stacked | Full links / menu |
| Mobile | 375px | 1 column | Stacked | Menu button |

No horizontal scrolling at any width.

### Accessibility Features

- Semantic HTML5 landmarks: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<form>`, `<footer>`
- Real interactive elements: `<a>`, `<button>`, `<input>`, `<textarea>`
- Every `<label>` is connected to its input using `for` and `id`
- Descriptive `alt` text on every image
- Visible **hover** states on links and buttons
- Visible **focus** outlines for keyboard users (Tab key navigation)
- Mobile menu button with `aria-label` and `aria-expanded`
- Text colour contrast meets WCAG AA

### Lighthouse Result

Accessibility score: **[your score]/100**

![Lighthouse Score](images/[your-lighthouse-screenshot].png)

---

## 📁 Project Structure

    campus-eats-website/
    ├── .vscode/
    │   └── mcp.json        # VS Code MCP config
    ├── .mcp.json           # Claude Code MCP config
    ├── images/             # Food photos and screenshots
    ├── index.html          # Main website
    └── README.md

---

## ▶️ How to Run Locally

1. Download or clone this repository:

       git clone [your GitHub repo link]

2. Open the folder and double-click `index.html` to open it in a browser.

No installation is needed.

---

## 🚀 Task 4: Deployment

The website is deployed on **Vercel** using the Vercel CLI:

    npx vercel --prod

---

## 👤 Author

**[Khadija Zahra]** – [BSEF22M511]
Human-Computer Interaction, Lab 07
Punjab University College of Information Technology (PUCIT), Lahore

**Image credits:** Food photos from [Unsplash / Pexels].
