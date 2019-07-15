---
ms.openlocfilehash: dab6b435a885d862d08f94dd31de79625f19bcc0
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870510"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="c5b06-101">Pokyny k instalaci – instalační program sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5b06-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="c5b06-102">Existují dva různé způsoby, jak najít **sada SDK platformy kompilátoru .NET** v **instalační program sady Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="c5b06-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="c5b06-103">Instalace pomocí instalačního programu sady Visual Studio – zobrazení úloh</span><span class="sxs-lookup"><span data-stu-id="c5b06-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="c5b06-104">Sada SDK platformy kompilátoru .NET nebude automaticky označen jako součást sady funkcí vývoj rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5b06-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="c5b06-105">Je třeba vybrat jako volitelnou komponentu.</span><span class="sxs-lookup"><span data-stu-id="c5b06-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="c5b06-106">Run **Visual Studio Installer**</span><span class="sxs-lookup"><span data-stu-id="c5b06-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="c5b06-107">Vyberte **upravit**</span><span class="sxs-lookup"><span data-stu-id="c5b06-107">Select **Modify**</span></span> 
1. <span data-ttu-id="c5b06-108">Zkontrolujte, **vývoj rozšíření sady Visual Studio** pracovního vytížení.</span><span class="sxs-lookup"><span data-stu-id="c5b06-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="c5b06-109">Otevřít **vývoj rozšíření sady Visual Studio** uzel ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="c5b06-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="c5b06-110">Zaškrtněte políčko u **sada SDK platformy kompilátoru .NET**.</span><span class="sxs-lookup"><span data-stu-id="c5b06-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="c5b06-111">Najdete ho naposledy pod volitelné součásti.</span><span class="sxs-lookup"><span data-stu-id="c5b06-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="c5b06-112">V případě potřeby je také vhodné **DGML editor** zobrazit grafy ve vizualizátoru:</span><span class="sxs-lookup"><span data-stu-id="c5b06-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="c5b06-113">Otevřít **jednotlivé komponenty** uzel ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="c5b06-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="c5b06-114">Zaškrtněte políčko u **DGML editor**</span><span class="sxs-lookup"><span data-stu-id="c5b06-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="c5b06-115">Instalace pomocí Visual Studio Installer - kartě jednotlivé komponenty</span><span class="sxs-lookup"><span data-stu-id="c5b06-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="c5b06-116">Run **Visual Studio Installer**</span><span class="sxs-lookup"><span data-stu-id="c5b06-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="c5b06-117">Vyberte **upravit**</span><span class="sxs-lookup"><span data-stu-id="c5b06-117">Select **Modify**</span></span> 
1. <span data-ttu-id="c5b06-118">Vyberte **jednotlivé komponenty** kartu</span><span class="sxs-lookup"><span data-stu-id="c5b06-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="c5b06-119">Zaškrtněte políčko u **sada SDK platformy kompilátoru .NET**.</span><span class="sxs-lookup"><span data-stu-id="c5b06-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="c5b06-120">Najdete v horní části stránky v části **sestavení kompilátory, nástroje a moduly runtime** oddílu.</span><span class="sxs-lookup"><span data-stu-id="c5b06-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="c5b06-121">V případě potřeby je také vhodné **DGML editor** zobrazit grafy ve vizualizátoru:</span><span class="sxs-lookup"><span data-stu-id="c5b06-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="c5b06-122">Zaškrtněte políčko u **DGML editor**.</span><span class="sxs-lookup"><span data-stu-id="c5b06-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="c5b06-123">Najdete ho pod **kódu nástroje** oddílu.</span><span class="sxs-lookup"><span data-stu-id="c5b06-123">You'll find it under the **Code tools** section.</span></span>
