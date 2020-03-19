---
title: Instalace F#
description: Naučte se, jak nainstalovat F# různými způsoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400244"
---
# <a name="install-f"></a><span data-ttu-id="56f82-103">Instalace F\#</span><span class="sxs-lookup"><span data-stu-id="56f82-103">Install F\#</span></span>

<span data-ttu-id="56f82-104">Můžete nainstalovat F# několika způsoby, v závislosti na vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="56f82-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="56f82-105">Instalace jazyka F# pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56f82-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="56f82-106">Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) poprvé, nejprve nainstaluje Instalační program sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56f82-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="56f82-107">Nainstalujte příslušnou edici sady Visual Studio od instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="56f82-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="56f82-108">Pokud už máte nainstalovaný Visual Studio, zvolte **Změnit** vedle edice, do které chcete přidat F#.</span><span class="sxs-lookup"><span data-stu-id="56f82-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="56f82-109">Na stránce Úlohy vyberte **úlohu vývoje ASP.NET a webu,** která zahrnuje podporu F# a .NET Core pro ASP.NET základní projekty.</span><span class="sxs-lookup"><span data-stu-id="56f82-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="56f82-110">Zvolte **Změnit** v pravém dolním rohu a nainstalujte vše, co jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="56f82-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="56f82-111">Potom můžete spustit Visual Studio s F# výběrem **Spustit** v Instalační službě sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56f82-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="56f82-112">Instalace jazyka F# s kódem sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56f82-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="56f82-113">Ujistěte se, že máte [na](https://git-scm.com/download) vaší cestě nainstalovaný git.</span><span class="sxs-lookup"><span data-stu-id="56f82-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="56f82-114">Zda je správně nainstalována, můžete `git --version` ji ověřit zadáním příkazového řádku a stisknutím **klávesy Enter**.</span><span class="sxs-lookup"><span data-stu-id="56f82-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="56f82-115">Nainstalujte [sadu](https://code.visualstudio.com) [.NET Core SDK](https://dotnet.microsoft.com/download) a kód sady Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="56f82-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="56f82-116">Vyberte ikonu Rozšíření a vyhledejte "Ionide":</span><span class="sxs-lookup"><span data-stu-id="56f82-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="56f82-117">Jediný modul plug-in potřebný pro podporu Jazyka F# v kódu sady Visual Studio je [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="56f82-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="56f82-118">Můžete však také nainstalovat [Ionide-FAKE,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) abyste získali [podporu FAKE](https://fake.build/) a [Ionide-Paket,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) abyste získali podporu [Paketu.](https://fsprojects.github.io/Paket/)</span><span class="sxs-lookup"><span data-stu-id="56f82-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="56f82-119">FAKE a Paket jsou další f# komunitní nástroje pro vytváření projektů a správu závislostí, resp.</span><span class="sxs-lookup"><span data-stu-id="56f82-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="56f82-120">Instalace Jazyka F# pomocí Visual Studia pro Mac</span><span class="sxs-lookup"><span data-stu-id="56f82-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="56f82-121">F# je ve výchozím nastavení nainstalován v [sadě Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.</span><span class="sxs-lookup"><span data-stu-id="56f82-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="56f82-122">Po dokončení instalace zvolte **Spustit Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="56f82-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="56f82-123">Visual Studio můžete otevřít taky ve Finderu v macOS.</span><span class="sxs-lookup"><span data-stu-id="56f82-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="56f82-124">Instalace jazyka F# na server sestavení</span><span class="sxs-lookup"><span data-stu-id="56f82-124">Install F# on a build server</span></span>

<span data-ttu-id="56f82-125">Pokud používáte rozhraní .NET Core nebo rozhraní .NET Framework prostřednictvím sady .NET SDK, stačí nainstalovat sadu .NET SDK na server sestavení.</span><span class="sxs-lookup"><span data-stu-id="56f82-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="56f82-126">Má vše, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="56f82-126">It has everything you need.</span></span>

<span data-ttu-id="56f82-127">Pokud používáte rozhraní .NET Framework a **nepoužíváte** sdk .NET SDK, budete muset nainstalovat [skladovou položku nástroje sady Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do systému Windows Server.</span><span class="sxs-lookup"><span data-stu-id="56f82-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="56f82-128">V instalačním programu vyberte **nástroje pro sestavení instalačního programu .NET**a potom vyberte komponentu **kompilátoru F#** na pravé straně nabídky instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="56f82-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
