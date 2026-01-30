# fetchanim

> Disclaimer: This project is purely made by AI (not really familiar with what I am doing so I got help from Claude), I just want to find a way to put a GIF in my fastfetch config.

A simple shell script that displays animated GIFs alongside system information using Kitty terminal's native image rendering capability and fastfetch.

<p align="center">
  <img src="./preview.png" alt="Kitty-Fetch Preview">
</p>

## ✨ Features

- **Native GIF rendering** using Kitty terminal's `icat` kitten
- **Dynamic sizing** - GIF height automatically matches fastfetch output
- **Full color support** - Preserves ANSI colors from fastfetch
- **Side-by-side layout** - GIF on the left, system info on the right
- **Lightweight** - Simple zsh script with minimal dependencies

## 📋 Requirements

- [Kitty Terminal](https://sw.kovidgoyal.net/kitty/) - Required for image rendering
- [Fastfetch](https://github.com/fastfetch-cli/fastfetch) - For system information
- Zsh shell

## 🚀 Installation

1. Clone this repository:

```bash
git clone https://github.com/novakamiii/fetchanim
cd fetchanim
```

1. Make the script executable:

```bash
chmod +x fetchanim
```

## 🎮 Usage

### Basic Usage

```bash
./fetchanim
```

### OPTIONAL: Add to your PATH

```bash
sudo cp fetchanim /usr/local/bin/
```

### OPTIONAL: If you use fish

```bash
# In ./home/$USER/.config/fish/config.fish
# Add this to the very top:

/home/$USER/(DIR where you cloned it...)/fetchanim/fetchanim
```

### Custom GIF Path

Edit the script and change the `GIF_PATH` variable:

```bash
GIF_PATH="/path/to/your/favorite.gif"
```

### Run on Terminal Startup

Add to your `~/.zshrc`:

```bash
# Run kitty-fetch on terminal startup
if [[ "$TERM" == "xterm-kitty" ]]; then
    /path/to/kitty-fetch
fi
```

## ⚙️ Configuration

You can customize the script by editing these variables:

| Variable          | Default                                             | Description                                                                      |
| ----------------- | --------------------------------------------------- | -------------------------------------------------------------------------------- |
| `GIF_PATH`        | `/home/nova/Pictures/brrtfetch/gifs/wuwa/lynae.gif` | Path to your GIF file                                                            |
| `IMG_WIDTH`       | `30`                                                | Width of the GIF in terminal columns (25-35 recommended)                         |
| `VERTICAL_OFFSET` | `2`                                                 | How many lines down to position the image (0 = top, increase to align with text) |
| `OFFSET`          | `IMG_WIDTH + 3`                                     | Horizontal spacing between GIF and text                                          |

### Example Customization

```bash
# Make the image larger
IMG_WIDTH=40

# Move image down to align with text (not the border)
VERTICAL_OFFSET=3

# Add more spacing between image and text
OFFSET=$((IMG_WIDTH + 5))
```

## 🎨 GIF Recommendations

For best results, use GIFs that:

- Have a **transparent or solid background**
- Are **square or portrait oriented** (not too wide)
- Have **clear details** that work well when scaled
- Are **under 5MB** for faster loading

## 🔧 Troubleshooting

### GIF not displaying

- Verify you're running in Kitty terminal: `echo $TERM` should show `xterm-kitty`
- Test if icat works: `kitten icat /path/to/your.gif`
- Check if the GIF path is correct

### Text overlapping with image

- Increase the `IMG_WIDTH` value
- Adjust the `OFFSET` calculation

### Colors not showing

- Make sure fastfetch is installed: `fastfetch --version`
- Try running fastfetch directly to verify colors work: `fastfetch --logo-type none`

### Image stretched or distorted

- Adjust `IMG_WIDTH` to better match your GIF's aspect ratio
- Try different width values (25, 30, 35, 40)

## 🤝 Acknowledgments

- Inspired by [brrtfetch](https://github.com/ferrebarrat/brrtfetch) - An animated ASCII art fetcher
- Uses [fastfetch](https://github.com/fastfetch-cli/fastfetch) for system information
- Built for [Kitty Terminal](https://sw.kovidgoyal.net/kitty/)

## 📝 License

MIT License - Feel free to use and modify as you like!

---

**Note**: This script is specifically designed for Kitty terminal and will not work in other terminals. For ASCII art-based fetchers that work in any terminal, check out the original [brrtfetch](https://github.com/ferrebarrat/brrtfetch) project.
