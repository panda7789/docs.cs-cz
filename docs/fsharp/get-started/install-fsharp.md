---
title: Instalace F#
description: Naučte se instalovat F# různými různými způsoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346568"
---
# <a name="install-f"></a><span data-ttu-id="b9524-103">Nainstalovat F\#</span><span class="sxs-lookup"><span data-stu-id="b9524-103">Install F\#</span></span>

<span data-ttu-id="b9524-104">V závislosti na F# vašem prostředí můžete instalovat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b9524-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="b9524-105">Instalace F# se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9524-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="b9524-106">Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) poprvé, nejprve se nainstaluje instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9524-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="b9524-107">Z instalačního programu nainstalujte odpovídající edici sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9524-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="b9524-108">Pokud již máte nainstalováno Visual Studio, klikněte na tlačítko **Upravit** vedle edice, kterou chcete přidat F# do nástroje.</span><span class="sxs-lookup"><span data-stu-id="b9524-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="b9524-109">Na stránce úlohy vyberte úlohu **vývoje ASP.NET a webu** , která zahrnuje F# a podporu .NET Core pro ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="b9524-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="b9524-110">V pravém dolním rohu vyberte **Upravit** a nainstalujte všechno, co jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="b9524-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="b9524-111">Pak můžete otevřít Visual Studio s F# výběrem možnosti **Spustit** v instalační program pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9524-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="b9524-112">Instalace F# pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b9524-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="b9524-113">Ujistěte se, že máte nainstalovaný [Git](https://git-scm.com/download) a máte k dispozici na vaší cestě.</span><span class="sxs-lookup"><span data-stu-id="b9524-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="b9524-114">Můžete ověřit, zda je správně nainstalován, zadáním `git --version` na příkazovém řádku a stisknutím klávesy **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="b9524-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="b9524-115">Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) a [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="b9524-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="b9524-116">Vyberte ikonu rozšíření a vyhledejte "Ionide":</span><span class="sxs-lookup"><span data-stu-id="b9524-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="b9524-117">Jediným modulem plug- F# in vyžadovaným pro podporu v Visual Studio Code je [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b9524-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="b9524-118">Můžete ale také nainstalovat [Ionide-falešné](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , abyste získali [falešnou](https://fake.build/) podporu a [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pro získání podpory [paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="b9524-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="b9524-119">NAPODOBENINy a paket jsou F# další komunitní nástroje pro vytváření projektů a správu závislostí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b9524-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="b9524-120">Instalace F# pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="b9524-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="b9524-121">F#je ve výchozím nastavení nainstalován v [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.</span><span class="sxs-lookup"><span data-stu-id="b9524-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="b9524-122">Po dokončení instalace vyberte **Spustit Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b9524-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="b9524-123">Můžete také otevřít Visual Studio prostřednictvím hledání na macOS.</span><span class="sxs-lookup"><span data-stu-id="b9524-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="b9524-124">Instalace F# na server sestavení</span><span class="sxs-lookup"><span data-stu-id="b9524-124">Install F# on a build server</span></span>

<span data-ttu-id="b9524-125">Pokud používáte .NET Core nebo .NET Framework přes sadu .NET SDK, stačí pouze nainstalovat sadu .NET SDK na server sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9524-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="b9524-126">Obsahuje všechno, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="b9524-126">It has everything you need.</span></span>

<span data-ttu-id="b9524-127">Pokud používáte .NET Framework a **nepoužíváte** sadu .NET SDK, bude nutné nainstalovat [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="b9524-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="b9524-128">V instalačním programu vyberte možnost **Nástroje pro vytváření desktopových prostředí .NET**a pak na pravé straně nabídky instalačního programu vyberte komponentu  **F# kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="b9524-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
