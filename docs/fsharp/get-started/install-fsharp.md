---
title: 'Instalaci F #'
description: 'Informace o instalaci F # založeny na vašem prostředí.'
ms.date: 08/28/2018
ms.openlocfilehash: d53ecdcba5411db62208cb683a0fad795711b77c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193900"
---
# <a name="install-f"></a><span data-ttu-id="f3763-103">Instalaci F #</span><span class="sxs-lookup"><span data-stu-id="f3763-103">Install F#</span></span> #

<span data-ttu-id="f3763-104">Můžete nainstalovat F # několika různými způsoby v závislosti na vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="f3763-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="f3763-105">Instalaci F # pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3763-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="f3763-106">Pokud stahujete [sady Visual Studio](https://visualstudio.microsoft.com/) poprvé, bude nejprve nainstalovat Instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3763-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="f3763-107">Instalace odpovídající SKU sady Visual Studio pomocí instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="f3763-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="f3763-108">Pokud už máte nainstalovaný, klikněte na tlačítko **změnit**.</span><span class="sxs-lookup"><span data-stu-id="f3763-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="f3763-109">Dále uvidíte seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="f3763-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="f3763-110">Vyberte **vývoj pro ASP.NET a web** instalace podporu F # a .NET Core pro projekty ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3763-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="f3763-111">Klepnutím na tlačítko **změnit** v dolní pravé straně.</span><span class="sxs-lookup"><span data-stu-id="f3763-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="f3763-112">Tím se nainstaluje všechno, co jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="f3763-112">This will install everything you have selected.</span></span> <span data-ttu-id="f3763-113">Pak můžete otevřít Visual Studio 2017 s podporou jazyka F # kliknutím **spuštění**.</span><span class="sxs-lookup"><span data-stu-id="f3763-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="f3763-114">Instalaci F # pomocí sady Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="f3763-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="f3763-115">F # je nainstalovaný ve výchozím nastavení v [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), bez ohledu na to, konfiguraci, kterou zvolíte.</span><span class="sxs-lookup"><span data-stu-id="f3763-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter which configuration you choose.</span></span>

<span data-ttu-id="f3763-116">Po dokončení instalace zvolte možnost "Spustit Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="f3763-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="f3763-117">Také ho můžete spustit v systému macOS prostřednictvím hledání.</span><span class="sxs-lookup"><span data-stu-id="f3763-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="f3763-118">Instalaci F # ve Visual Studiu Code</span><span class="sxs-lookup"><span data-stu-id="f3763-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="f3763-119">Musíte mít [nainstalovaný git](https://git-scm.com/download) a dostupný na vaší cesty pomocí šablon projektu.</span><span class="sxs-lookup"><span data-stu-id="f3763-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="f3763-120">Můžete ověřit, jestli je správně nainstalovaný zadáním `git --version` na příkazovém řádku a stisknutím klávesy **Enter**.</span><span class="sxs-lookup"><span data-stu-id="f3763-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="f3763-121">macOS</span><span class="sxs-lookup"><span data-stu-id="f3763-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="f3763-122">[Mono](https://www.mono-project.com) se používá pro [F # Interactive](../tutorials/fsharp-interactive/index.md) podporovat.</span><span class="sxs-lookup"><span data-stu-id="f3763-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="f3763-123">Pomocí Homebrew je nejjednodušší způsob, jak nainstalovat Mono v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="f3763-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="f3763-124">Jednoduše do svého terminálu zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f3763-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="f3763-125">Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="f3763-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="f3763-126">Linux</span><span class="sxs-lookup"><span data-stu-id="f3763-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="f3763-127">[Mono](https://www.mono-project.com) se používá pro [F # Interactive](../tutorials/fsharp-interactive/index.md) podporovat.</span><span class="sxs-lookup"><span data-stu-id="f3763-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="f3763-128">Pokud jste v systému Debian nebo Ubuntu, můžete použít následující:</span><span class="sxs-lookup"><span data-stu-id="f3763-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="f3763-129">Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="f3763-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="f3763-130">Windows</span><span class="sxs-lookup"><span data-stu-id="f3763-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="f3763-131">Nainstalujte [Visual Studio s podporou F #](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f3763-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="f3763-132">Tím se nainstaluje všechny komponenty potřebné k zápisu, kompilaci a spouštění kódu jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="f3763-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="f3763-133">Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="f3763-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="f3763-134">Bude nutné [Visual Studio Code](https://code.visualstudio.com) nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f3763-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="f3763-135">Dále klikněte na ikonu rozšíření a vyhledejte položku "Ionide":</span><span class="sxs-lookup"><span data-stu-id="f3763-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="f3763-136">Pouze modul plug-in, které jsou potřebné pro podporu F # v aplikaci Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="f3763-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="f3763-137">Ale můžete také nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) zobrazíte [FALEŠNÉ](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) zobrazíte [Stáhnout](https://fsprojects.github.io/Paket/) podporovat.</span><span class="sxs-lookup"><span data-stu-id="f3763-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="f3763-138">FALEŠNÉ a stáhnout jsou další F # komunitní nástroje pro vytváření projektů a správu závislostí, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f3763-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>
