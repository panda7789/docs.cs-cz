---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526738"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="240a3-101">Pokyny k instalaci – Instalační služba sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="240a3-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="240a3-102">Existují dva různé způsoby, jak najít **sdk platformy kompilátoru .NET** v **Instalační službě sady Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="240a3-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="240a3-103">Instalace pomocí instalačního programu sady Visual Studio – zobrazení úloh</span><span class="sxs-lookup"><span data-stu-id="240a3-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="240a3-104">Sada SDK platformy kompilátoru .NET není automaticky vybrána jako součást vývojového zatížení rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="240a3-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="240a3-105">Je nutné ji vybrat jako volitelnou součást.</span><span class="sxs-lookup"><span data-stu-id="240a3-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="240a3-106">Spuštění **instalačního programu sady Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="240a3-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="240a3-107">Vybrat **změnit**</span><span class="sxs-lookup"><span data-stu-id="240a3-107">Select **Modify**</span></span>
1. <span data-ttu-id="240a3-108">Zkontrolujte zatížení **vývoje rozšíření Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="240a3-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="240a3-109">Otevřete uzel **vývoje rozšíření Visual Studio** ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="240a3-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="240a3-110">Zaškrtněte políčko **u sady .NET Compiler Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="240a3-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="240a3-111">Najdete ji jako poslední pod volitelnými součástmi.</span><span class="sxs-lookup"><span data-stu-id="240a3-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="240a3-112">Volitelně budete také chtít, aby **editor DGML** zobrazoval grafy ve vizualizéru:</span><span class="sxs-lookup"><span data-stu-id="240a3-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="240a3-113">Otevřete uzel **jednotlivých komponent** ve stromu souhrnu.</span><span class="sxs-lookup"><span data-stu-id="240a3-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="240a3-114">Zaškrtněte políčko **pro editor DGML**</span><span class="sxs-lookup"><span data-stu-id="240a3-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="240a3-115">Instalace pomocí karty Instalační služba sady Visual Studio – jednotlivé součásti</span><span class="sxs-lookup"><span data-stu-id="240a3-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="240a3-116">Spuštění **instalačního programu sady Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="240a3-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="240a3-117">Vybrat **změnit**</span><span class="sxs-lookup"><span data-stu-id="240a3-117">Select **Modify**</span></span>
1. <span data-ttu-id="240a3-118">Výběr karty **Jednotlivé komponenty**</span><span class="sxs-lookup"><span data-stu-id="240a3-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="240a3-119">Zaškrtněte políčko **u sady .NET Compiler Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="240a3-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="240a3-120">Najdete ji v horní části **kompilátory, vytvářet nástroje a runtimes** části.</span><span class="sxs-lookup"><span data-stu-id="240a3-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="240a3-121">Volitelně budete také chtít, aby **editor DGML** zobrazoval grafy ve vizualizéru:</span><span class="sxs-lookup"><span data-stu-id="240a3-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="240a3-122">Zaškrtněte políčko **pro editor DGML**.</span><span class="sxs-lookup"><span data-stu-id="240a3-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="240a3-123">Najdete ji v části **Nástroje kódu.**</span><span class="sxs-lookup"><span data-stu-id="240a3-123">You'll find it under the **Code tools** section.</span></span>
