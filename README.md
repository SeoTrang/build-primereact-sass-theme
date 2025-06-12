Here’s the updated version of your guide with all the adjustments you asked for:

---

# 🧩 Building a Custom PrimeReact Theme with SCSS

This guide explains how to create and build a custom theme for [PrimeReact](https://primereact.org) using the official [SASS theme infrastructure](https://github.com/primefaces/primereact-sass-theme).

---

## 📦 Prerequisites

Ensure you have the following installed:

* [Node.js](https://nodejs.org) (v14+ recommended)
* [SASS](https://sass-lang.com/install) (Dart Sass or via `npm i -g sass`)

Install globally (if not already):

```bash
npm install -g sass
```

---

## 📁 Project Structure

Clone the official theme repository:

```bash
git clone https://github.com/primefaces/primereact-sass-theme.git
cd primereact-sass-theme
```

The structure:

```
primereact-sass-theme/
├── theme-base/               # Base SCSS shared by all themes
├── themes/                   # Existing built-in themes
├── my-themes/                # Your custom themes
├── dist/                     # Compiled CSS output
├── build.sh / build.bat      # Optional batch build scripts
```

---

## 🎨 Create Your Custom Theme

### 1. Create a new folder in `my-themes/`:

```bash
mkdir my-themes/lara-light-green-hunonic
```

### 2. Copy a base theme

Copy an existing theme (e.g. green) from:

```
./themes/lara/lara-light/green/
```

Into your new folder:

```
my-themes/lara-light-green-hunonic/
```

Make sure to copy:

* `_variables.scss`
* `_extensions.scss`
* `_fonts.scss` (optional, if needed)
* `theme.scss` (or create your own as below)

### 3. Edit `theme.scss` in `my-themes/lara-light-green-hunonic`:

```scss
// theme.scss

$primaryColor: #00b33d !default;
$primaryLightColor: #b2f2d3 !default; // Bạn có thể thay nếu muốn sáng hơn
$primaryDarkColor: #61bc3f !default;  // màu phụ hoặc màu hover
$primaryDarkerColor: #049d36 !default; // đậm hơn nữa nếu cần
$primaryTextColor: #ffffff !default;

$highlightBg: #f0fdfa !default;
$highlightTextColor: $primaryDarkerColor !default;
$highlightFocusBg: rgba($primaryColor, 0.2) !default;

// Import PrimeReact SASS cấu trúc
@import "./_variables";
@import "./_fonts";
@import "../../theme-base/_components";
@import "./_extensions";
```

Feel free to adjust colors and override variables in `_variables.scss` to reflect your company’s branding.

---

## 🛠 Build the Theme

Compile your theme using the `sass` CLI:

```bash
sass my-themes/lara-light-green-hunonic/theme.scss dist/themes/lara-light-green-hunonic/theme.css
```

For minified output:

```bash
sass my-themes/lara-light-green-hunonic/theme.scss dist/themes/lara-light-green-hunonic/theme.min.css --style=compressed
```

---

## ✅ Use in Your React App

1. Import the compiled CSS file in your React app:

```tsx
import 'path/to/dist/themes/lara-light-green-hunonic/theme.css';
```

2. Use PrimeReact components as usual — they will automatically use your custom theme.

---

## 📌 Tips

* Use a theme from `themes/lara` as a starting point.
* Customize `_variables.scss` for color and spacing control.
* Use `_fonts.scss` to define or override custom font styles.
* Don’t forget to rebuild the theme after making SCSS changes.

---

## 📚 Resources

* [PrimeReact Theming Docs](https://primereact.org/theming/)
* [SASS Language Guide](https://sass-lang.com/documentation/)
* [PrimeReact GitHub](https://github.com/primefaces/primereact)
* [Origin Repo](https://github.com/primefaces/primereact-sass-theme)

---

Let me know if you'd like this saved to a `README.md` file or want to add automated build commands or VS Code snippets.
