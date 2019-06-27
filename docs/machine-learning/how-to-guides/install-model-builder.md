---
title: Instalace Tvůrce modelu
description: Zjistěte, jak nainstalovat nástroj Tvůrce modelu ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410650"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="10a69-103">Instalace Tvůrce modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="10a69-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="10a69-104">Zjistěte, jak nainstalovat Tvůrce modelu ML.NET přidání machine learningu do aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="10a69-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="10a69-105">Tvůrce modelu je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="10a69-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="10a69-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10a69-106">Pre-requisites</span></span>

- <span data-ttu-id="10a69-107">Visual Studio 2017 15.9.12 nebo vyšší / Visual Studio. 2019</span><span class="sxs-lookup"><span data-stu-id="10a69-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="10a69-108">.NET core 2.1 nebo novější sady SDK</span><span class="sxs-lookup"><span data-stu-id="10a69-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="10a69-109">Omezení</span><span class="sxs-lookup"><span data-stu-id="10a69-109">Limitations</span></span>

- <span data-ttu-id="10a69-110">Rozšíření Tvůrce modelu ML.NET aktuálně funguje pouze v sadě Visual Studio na Windows.</span><span class="sxs-lookup"><span data-stu-id="10a69-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="10a69-111">Trénovací datové sady limit 1GB</span><span class="sxs-lookup"><span data-stu-id="10a69-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="10a69-112">SQL Server má limit 100 tisíc řádků pro školení</span><span class="sxs-lookup"><span data-stu-id="10a69-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="10a69-113">Microsoft SQL Server Data Tools pro Visual Studio 2017 se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="10a69-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="10a69-114">Instalace</span><span class="sxs-lookup"><span data-stu-id="10a69-114">Install</span></span>

<span data-ttu-id="10a69-115">Tvůrce modelu ML.NET se dají nainstalovat přes Visual Studio Marketplace nebo v rámci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10a69-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="10a69-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="10a69-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="10a69-117">Stáhnout z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="10a69-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="10a69-118">Postupujte podle pokynů k instalaci na příslušnou verzi sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10a69-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="10a69-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10a69-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="10a69-120">V panelu nabídek vyberte **nástroje** > **rozšíření a aktualizace**</span><span class="sxs-lookup"><span data-stu-id="10a69-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="10a69-121">Uvnitř *rozšíření a aktualizace* příkazový řádek, vyberte *Online* uzlu.</span><span class="sxs-lookup"><span data-stu-id="10a69-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="10a69-122">Na panelu hledání vyhledejte *Tvůrce modelu ML.NET* a ve výsledcích vyberte ML.NET Tvůrce modelu (Preview)</span><span class="sxs-lookup"><span data-stu-id="10a69-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="10a69-123">Postupujte podle pokynů k dokončení instalace</span><span class="sxs-lookup"><span data-stu-id="10a69-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="10a69-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="10a69-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="10a69-125">Na panelu nabídek vyberte **rozšíření** > **spravovat rozšíření**</span><span class="sxs-lookup"><span data-stu-id="10a69-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="10a69-126">Uvnitř *rozšíření a aktualizace* příkazový řádek, vyberte *Online* uzlu.</span><span class="sxs-lookup"><span data-stu-id="10a69-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="10a69-127">Typ *Tvůrce modelu ML.NET* do panelu vyhledávání vyberte ML.NET Tvůrce modelu (Preview)</span><span class="sxs-lookup"><span data-stu-id="10a69-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="10a69-128">Postupujte podle pokynů k dokončení instalace</span><span class="sxs-lookup"><span data-stu-id="10a69-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="10a69-129">Odinstalovat</span><span class="sxs-lookup"><span data-stu-id="10a69-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="10a69-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10a69-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="10a69-131">Na panelu nabídek vyberte **nástroje** > **rozšíření a aktualizace**</span><span class="sxs-lookup"><span data-stu-id="10a69-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="10a69-132">Uvnitř *rozšíření a aktualizace* výzvu, rozbalte *nainstalováno* uzel a vyberte možnost *nástroje*</span><span class="sxs-lookup"><span data-stu-id="10a69-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="10a69-133">Ze seznamu nástrojů vyberte ML.NET Tvůrce modelu (Preview) a pak vyberte *odinstalace*</span><span class="sxs-lookup"><span data-stu-id="10a69-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="10a69-134">Postupujte podle pokynů k dokončení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="10a69-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="10a69-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="10a69-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="10a69-136">Na panelu nabídek vyberte **rozšíření** > **spravovat rozšíření**</span><span class="sxs-lookup"><span data-stu-id="10a69-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="10a69-137">Uvnitř *rozšíření a aktualizace* výzvu, rozbalte *nainstalováno* uzel a vyberte možnost *nástroje*</span><span class="sxs-lookup"><span data-stu-id="10a69-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="10a69-138">Ze seznamu nástrojů vyberte ML.NET Tvůrce modelu (Preview) a pak vyberte *odinstalace*</span><span class="sxs-lookup"><span data-stu-id="10a69-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="10a69-139">Postupujte podle pokynů k dokončení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="10a69-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="10a69-140">Upgrade</span><span class="sxs-lookup"><span data-stu-id="10a69-140">Upgrade</span></span>

<span data-ttu-id="10a69-141">Proces upgradu je podobný procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="10a69-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="10a69-142">Stáhněte si nejnovější verzi z webu Visual Studio Marketplace nebo pomocí Správce rozšíření v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10a69-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
