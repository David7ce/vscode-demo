# VSCode instalación

## Cómo se instala
Visual Studio Code se publica bajo dos versiones:

- VS Code como producto de Microsoft, es la versión de GitHub con trackers y alguna característica extra añadida por MS.
- "Code OSS" como software libre de código abierto, desarrollada en GitHub por los trabajadores de Microsoft y la comunidad.

### VS Code de MicroSoft
Para instalar la versión de Visual Studio Code de Microsoft, tenemos que descargar el ejecutable de [VS Code](https://code.visualstudio.com/#alt-downloads) desde la web oficial de MicroSoft. Esta versión está disponible para Windows (como exe), para macOS (dmg) y para Linux (.deb y .rpm)

- También podemos usar un instalador de paquetes en Windows como 'winget' o [chocolatey](https://community.chocolatey.org/packages/vscode)
```bash
$ winget install -e --id Microsoft.VisualStudioCode
$ choco install vscode
```

- [Brew](https://brew.sh) instalador de paquetes para macOS y Linux
```sh
brew install --cask visual-studio-code
```

- Y para Arch Linux:
```sh
git clone https://aur.archlinux.org/visual-studio-code-bin.git
cd visual-studio-code-bin
makepkg -si
```

### Code OSS
Para descargar la versión de código abierta tenemos que compilar la aplicación o usar algún método que lo haga previamente. Más info en el [repo de Microsoft](https://github.com/microsoft/vscode/wiki/How-to-Contribute))

Logo de Code OSS, 
![](./img/code-oss.png)

Para compilar la app desde el código fuente puedes usar la guía de MS [aquí](https://github.com/microsoft/vscode/wiki/How-to-Contribute#build-and-run).

- Los prerequisitos son: 
  - git, node .js, yarn, python
  - compilador C/C++
    - Windows: Windows Build Tools (with npm)
    - macOS: Xcode with gcc and make, run `xcode select --install`
    - Linux (building .deb and .rpm requires fakeroor and rpm)
      - Debian (deb): `sudo apt-get install build-essential g++ libx11-dev libxkbfile-dev libsecret-1-dev python-is-python3`
      - Red-Hat based (rpm): `sudo yum groupinstall "Development Tools" && sudo yum install libX11-devel.x86_64 libxkbfile-devel.x86_64 libsecret-devel # or .i686`
      - Others: make pkg-config gcc 

```sh
git clone https://github.com/microsoft/vscode
cd vscode
yarn
yarn watch
```

- Para sistemas Unix (Linux y macOS)
```sh
./scripts/code.sh
./scripts/code-cli.sh # for running CLI commands (eg --version)
```

- Para sistemas Windows
```sh
./scripts/code.bat
./scripts/code-cli.bat
```

- En Arch Linux la versión por defecto en los repositorios oficiales es ["Code OSS"](https://archlinux.org/packages/extra/x86_64/code/) y para instalarla solo habría que hacer uso de su gestor de paquetes 'pacman'.
```bash
sudo pacman -S code
```


## Referencias

- Wikipedia:
    - [Visual Studio Code - ArchWiki](https://wiki.archlinux.org/title/Visual_Studio_Code)
	- [Visual Studio Code - Wikipedia](https://es.wikipedia.org/wiki/Visual_Studio_Code)
	- [Chromium - Wikipedia](https://es.wikipedia.org/wiki/Chromium_(navegador))
	- [Electron (software framework) - Wikipedia](https://en.wikipedia.org/wiki/Electron_(software_framework))
	- [Node.js - Wikipedia](https://es.wikipedia.org/wiki/Node.js)
	- [JS engine - Wikipedia](https://en.wikipedia.org/wiki/V8_(JavaScript_engine))

- Herramientas VS Code:
	- [Chromium](https://www.chromium.org/chromium-projects/)
		- [Electron JS](https://www.electronjs.org/)
		- [Node JS](https://nodejs.org/en)
		- [V8](https://v8.dev/)

- Repositorios de código abierto:
	- [microsoft/vscode · GitHub](https://github.com/microsoft/vscode)
	- [electron/electron · GitHub](https://github.com/electron/electron)
	- [nodejs/node· GitHub](https://github.com/nodejs/node)
	- [google/chromium · git](https://chromium.googlesource.com/chromium/src)


- VS Code (aplicación escritorio):
	- [VS Code (Microsoft)](https://code.visualstudio.com/)
	- [VSCodium](https://vscodium.com/)

- VS Code (aplicación web):
	- [VS Code (entorno web)](https://vscode.dev/)
	- [VS Code (github)](https://github.dev/)

- VS Code con gestor de paquetes:
	- [VS Code - FreeBSD](https://www.freshports.org/editors/vscode#packages)
	- [VS Code - Gentoo](https://packages.gentoo.org/packages/app-editors/vscode)
	- [VS Code - AUR](https://aur.archlinux.org/packages/visual-studio-code-bin)
	- [VSCode - brew](https://formulae.brew.sh/cask/visual-studio-code)
	- [VSCode - AppImage](https://github.com/valicm/VSCode-AppImage)
	- [VSCode - pkgs](https://pkgs.org/search/?q=vscode)
	- [Code - Snapcraft](https://snapcraft.io/code)
	- [Code OSS - Archlinux](https://archlinux.org/packages/extra/x86_64/code/)
	- [Code OSS - FlatHub](https://flathub.org/apps/com.visualstudio.code-oss)
	- [VSCodium - FlatHub](https://flathub.org/apps/com.vscodium.codium)
