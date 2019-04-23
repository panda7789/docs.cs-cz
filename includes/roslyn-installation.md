---
ms.openlocfilehash: 72acd0029d0189de1c724856572957f111b9d18f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803714"
---
## <a name="installation-instructions"></a><span data-ttu-id="0b6a6-101">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="0b6a6-101">Installation instructions</span></span> 

<span data-ttu-id="0b6a6-102">Existují dva různé způsoby, jak najít **sada SDK platformy kompilátoru .NET** v **instalační program sady Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="0b6a6-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-workloads-view"></a><span data-ttu-id="0b6a6-103">Instalace pomocí zobrazení úloh</span><span class="sxs-lookup"><span data-stu-id="0b6a6-103">Install using the Workloads view</span></span>

<span data-ttu-id="0b6a6-104">Sada SDK platformy kompilátoru .NET nebude automaticky označen jako součást sady funkcí vývoj rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="0b6a6-105">Je třeba vybrat jako volitelnou komponentu.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="0b6a6-106">Run **Visual Studio Installer**</span><span class="sxs-lookup"><span data-stu-id="0b6a6-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="0b6a6-107">Vyberte **upravit**</span><span class="sxs-lookup"><span data-stu-id="0b6a6-107">Select **Modify**</span></span> 
1. <span data-ttu-id="0b6a6-108">Zkontrolujte, **vývoj rozšíření sady Visual Studio** pracovního vytížení.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="0b6a6-109">Otevřít **vývoj rozšíření sady Visual Studio** uzel ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="0b6a6-110">Zaškrtněte políčko u **sada SDK platformy kompilátoru .NET**.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="0b6a6-111">Najdete ho naposledy pod volitelné součásti.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="0b6a6-112">V případě potřeby je také vhodné **DGML editor** zobrazit grafy ve vizualizátoru:</span><span class="sxs-lookup"><span data-stu-id="0b6a6-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="0b6a6-113">Otevřít **jednotlivé komponenty** uzel ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="0b6a6-114">Zaškrtněte políčko u **DGML editor**</span><span class="sxs-lookup"><span data-stu-id="0b6a6-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-individual-components-tab"></a><span data-ttu-id="0b6a6-115">Instalace na kartě jednotlivé komponenty</span><span class="sxs-lookup"><span data-stu-id="0b6a6-115">Install using the Individual components tab</span></span>

1. <span data-ttu-id="0b6a6-116">Run **Visual Studio Installer**</span><span class="sxs-lookup"><span data-stu-id="0b6a6-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="0b6a6-117">Vyberte **upravit**</span><span class="sxs-lookup"><span data-stu-id="0b6a6-117">Select **Modify**</span></span> 
1. <span data-ttu-id="0b6a6-118">Vyberte **jednotlivé komponenty** kartu</span><span class="sxs-lookup"><span data-stu-id="0b6a6-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="0b6a6-119">Zaškrtněte políčko u **sada SDK platformy kompilátoru .NET**.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="0b6a6-120">Najdete v horní části stránky v části **sestavení kompilátory, nástroje a moduly runtime** oddílu.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="0b6a6-121">V případě potřeby je také vhodné **DGML editor** zobrazit grafy ve vizualizátoru:</span><span class="sxs-lookup"><span data-stu-id="0b6a6-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="0b6a6-122">Zaškrtněte políčko u **DGML editor**.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="0b6a6-123">Najdete ho pod **kódu nástroje** oddílu.</span><span class="sxs-lookup"><span data-stu-id="0b6a6-123">You'll find it under the **Code tools** section.</span></span>
