---
title: Instalace F#
description: Přečtěte si, F# jak nainstalovat na základě vašeho prostředí.
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855801"
---
# <a name="install-f"></a><span data-ttu-id="e3d0d-103">Nainstalovat F\#</span><span class="sxs-lookup"><span data-stu-id="e3d0d-103">Install F\#</span></span>

<span data-ttu-id="e3d0d-104">V závislosti na F# vašem prostředí můžete instalovat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="e3d0d-105">Instalace F# se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3d0d-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="e3d0d-106">Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) poprvé, nainstaluje se nejprve instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="e3d0d-107">Z instalačního programu nainstalujte příslušnou SKU sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="e3d0d-108">Pokud již máte nainstalováno, klikněte na tlačítko **Upravit**.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="e3d0d-109">Zobrazí se další seznam úloh.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="e3d0d-110">Vyberte **ASP.NET a vývoj pro web** , které F# budou instalovat podporu a podporu .net Core pro projekty ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="e3d0d-111">Potom v pravé dolní části klikněte na **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="e3d0d-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="e3d0d-112">Tím se nainstaluje všechno, co jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-112">This will install everything you have selected.</span></span> <span data-ttu-id="e3d0d-113">Pak můžete otevřít Visual Studio 2017 s F# podporou jazyka kliknutím na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="e3d0d-114">Instalace F# pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="e3d0d-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="e3d0d-115">F#je ve výchozím nastavení nainstalován v [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="e3d0d-116">Po dokončení instalace klikněte na spustit Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="e3d0d-117">Můžete ho také spustit pomocí hledání na macOS.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="e3d0d-118">Instalace F# pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e3d0d-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="e3d0d-119">Aby bylo možné používat šablony projektů, je nutné mít v cestě [nainstalovaný Git](https://git-scm.com/download) a k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="e3d0d-120">To, jestli je správně nainstalovaný, můžete ověřit zadáním `git --version` příkazu na příkazovém řádku a stisknutím klávesy **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="e3d0d-121">macOS</span><span class="sxs-lookup"><span data-stu-id="e3d0d-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="e3d0d-122">[Mono](https://www.mono-project.com) se používá pro [ F# interaktivní](../tutorials/fsharp-interactive/index.md) podporu.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="e3d0d-123">Nejjednodušší způsob, jak nainstalovat mono na macOS, je prostřednictvím homebrew.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="e3d0d-124">Do terminálu stačí zadat následující:</span><span class="sxs-lookup"><span data-stu-id="e3d0d-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="e3d0d-125">Nainstalujte také [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e3d0d-125">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="e3d0d-126">Linux</span><span class="sxs-lookup"><span data-stu-id="e3d0d-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="e3d0d-127">[Mono](https://www.mono-project.com) se používá pro [ F# interaktivní](../tutorials/fsharp-interactive/index.md) podporu.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="e3d0d-128">Pokud používáte Debian nebo Ubuntu, můžete použít následující:</span><span class="sxs-lookup"><span data-stu-id="e3d0d-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="e3d0d-129">Nainstalujte také [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e3d0d-129">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="e3d0d-130">Windows</span><span class="sxs-lookup"><span data-stu-id="e3d0d-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="e3d0d-131">Nainstalujte [Visual Studio s F# podporou](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e3d0d-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="e3d0d-132">Tím se nainstaluje všechny nezbytné komponenty pro zápis, kompilování a spouštění F# kódu.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="e3d0d-133">Nainstalujte také [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e3d0d-133">Also install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

---

<span data-ttu-id="e3d0d-134">Pak budete potřebovat [Visual Studio Code](https://code.visualstudio.com) nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="e3d0d-135">Potom klikněte na ikonu rozšíření a vyhledejte "Ionide":</span><span class="sxs-lookup"><span data-stu-id="e3d0d-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="e3d0d-136">Jediným modulem plug- F# in vyžadovaným pro podporu v Visual Studio Code je [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="e3d0d-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="e3d0d-137">Můžete ale také nainstalovat [Ionide-falešné](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , abyste získali [falešnou](https://fsharp.github.io/FAKE/) podporu a [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pro získání podpory [paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="e3d0d-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="e3d0d-138">NAPODOBENINy a paket jsou F# další komunitní nástroje pro vytváření projektů a správu závislostí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="e3d0d-139">Instalace F# na server sestavení</span><span class="sxs-lookup"><span data-stu-id="e3d0d-139">Install F# on a Build Server</span></span>

<span data-ttu-id="e3d0d-140">Pokud používáte .NET Core nebo .NET Framework přes sadu .NET SDK, stačí pouze nainstalovat sadu .NET SDK na server sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-140">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="e3d0d-141">Obsahuje všechno, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-141">It has everything you need.</span></span>

<span data-ttu-id="e3d0d-142">Pokud **používáte .NET Framework a nepoužíváte** sadu .NET SDK, bude nutné nainstalovat [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="e3d0d-142">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="e3d0d-143">V instalačním programu vyberte možnost **Nástroje pro vytváření desktopových prostředí .NET** a pak na pravé straně nabídky instalačního programu vyberte komponentu  **F# kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="e3d0d-143">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
