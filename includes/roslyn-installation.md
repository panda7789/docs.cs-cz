---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526738"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="d4155-101">Pokyny k instalaci – Instalační program pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d4155-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="d4155-102">Existují dva různé způsoby, jak **.NET Compiler Platform sadu SDK** v **instalační program pro Visual Studio**najít:</span><span class="sxs-lookup"><span data-stu-id="d4155-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="d4155-103">Instalace pomocí zobrazení Instalační program pro Visual Studio-úlohy</span><span class="sxs-lookup"><span data-stu-id="d4155-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="d4155-104">Sada .NET Compiler Platform SDK není automaticky vybraná jako součást úlohy vývoje rozšíření sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4155-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="d4155-105">Je nutné ji vybrat jako volitelnou součást.</span><span class="sxs-lookup"><span data-stu-id="d4155-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="d4155-106">Spustit **instalační program pro Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="d4155-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="d4155-107">Vybrat **Upravit**</span><span class="sxs-lookup"><span data-stu-id="d4155-107">Select **Modify**</span></span>
1. <span data-ttu-id="d4155-108">Projděte si úlohu **vývoj rozšíření sady Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="d4155-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="d4155-109">Ve stromové struktuře souhrnu otevřete uzel **vývoj rozšíření sady Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="d4155-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="d4155-110">Zaškrtněte políčko pro **sadu .NET Compiler Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="d4155-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="d4155-111">V rámci volitelných komponent najdete ho jako poslední.</span><span class="sxs-lookup"><span data-stu-id="d4155-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="d4155-112">Volitelně také budete chtít, aby **Editor DGML** zobrazoval grafy v Vizualizér:</span><span class="sxs-lookup"><span data-stu-id="d4155-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="d4155-113">Ve stromové struktuře souhrnu otevřete uzel **jednotlivé komponenty** .</span><span class="sxs-lookup"><span data-stu-id="d4155-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="d4155-114">Zaškrtněte políčko pro **Editor DGML** .</span><span class="sxs-lookup"><span data-stu-id="d4155-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="d4155-115">Instalace pomocí karty Instalační program pro Visual Studio – jednotlivé komponenty</span><span class="sxs-lookup"><span data-stu-id="d4155-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="d4155-116">Spustit **instalační program pro Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="d4155-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="d4155-117">Vybrat **Upravit**</span><span class="sxs-lookup"><span data-stu-id="d4155-117">Select **Modify**</span></span>
1. <span data-ttu-id="d4155-118">Výběr karty **jednotlivé součásti**</span><span class="sxs-lookup"><span data-stu-id="d4155-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="d4155-119">Zaškrtněte políčko pro **sadu .NET Compiler Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="d4155-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="d4155-120">Najdete ho nahoře v části **kompilátory, nástroje sestavení a moduly runtime** .</span><span class="sxs-lookup"><span data-stu-id="d4155-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="d4155-121">Volitelně také budete chtít, aby **Editor DGML** zobrazoval grafy v Vizualizér:</span><span class="sxs-lookup"><span data-stu-id="d4155-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="d4155-122">Zaškrtněte políčko pro **Editor DGML**.</span><span class="sxs-lookup"><span data-stu-id="d4155-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="d4155-123">Najdete ho v části **nástroje kódu** .</span><span class="sxs-lookup"><span data-stu-id="d4155-123">You'll find it under the **Code tools** section.</span></span>
