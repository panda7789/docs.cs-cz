---
title: Jak nainstalovat Tvůrce modelů
description: Zjistěte, jak nainstalovat nástroj ML.NET model Builder.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b87f712ad7a8b2229c1d42db4bad1fe511475ac7
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552945"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="0acf4-103">Postup instalace Tvůrce modelů ML.NET</span><span class="sxs-lookup"><span data-stu-id="0acf4-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="0acf4-104">Naučte se instalovat tvůrce modelů ML.NET a přidat do aplikací .NET strojové učení.</span><span class="sxs-lookup"><span data-stu-id="0acf4-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="0acf4-105">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="0acf4-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0acf4-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0acf4-106">Prerequisites</span></span>

- <span data-ttu-id="0acf4-107">Visual Studio 2017 verze 15.9.12 nebo novější/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0acf4-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="0acf4-108">.NET Core 2,1 SDK nebo novější.</span><span class="sxs-lookup"><span data-stu-id="0acf4-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="0acf4-109">Sada .NET Core 3,0 SDK není v současné době podporovaná.</span><span class="sxs-lookup"><span data-stu-id="0acf4-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="0acf4-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="0acf4-110">Limitations</span></span>

- <span data-ttu-id="0acf4-111">Rozšíření tvůrce modelů ML.NET je aktuálně funguje pouze v sadě Visual Studio ve Windows.</span><span class="sxs-lookup"><span data-stu-id="0acf4-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="0acf4-112">Školení pro datovou sadu o velikosti 1 GB</span><span class="sxs-lookup"><span data-stu-id="0acf4-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="0acf4-113">SQL Server má limit 100 000 řádků pro školení</span><span class="sxs-lookup"><span data-stu-id="0acf4-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="0acf4-114">Microsoft SQL Server Data Tools for Visual Studio 2017 se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="0acf4-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="0acf4-115">Instalace produktu</span><span class="sxs-lookup"><span data-stu-id="0acf4-115">Install</span></span>

<span data-ttu-id="0acf4-116">Tvůrce modelů ML.NET se dá nainstalovat buď prostřednictvím Visual Studio Marketplace, nebo v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0acf4-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="0acf4-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="0acf4-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="0acf4-118">Stáhnout z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="0acf4-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="0acf4-119">Podle zobrazených výzev nainstalujte do příslušné verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0acf4-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="0acf4-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0acf4-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="0acf4-121">V řádku nabídek vyberte **nástroje** > **rozšíření a aktualizace** .</span><span class="sxs-lookup"><span data-stu-id="0acf4-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Dialogové okno VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="0acf4-123">V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.</span><span class="sxs-lookup"><span data-stu-id="0acf4-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="0acf4-124">Na panelu hledání vyhledejte *Tvůrce modelů ml.NET* a z výsledků vyberte ml.NET model Builder (Preview).</span><span class="sxs-lookup"><span data-stu-id="0acf4-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="0acf4-126">Podle pokynů dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="0acf4-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="0acf4-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0acf4-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="0acf4-128">Na řádku nabídek vyberte **rozšíření** > **Spravovat rozšíření** .</span><span class="sxs-lookup"><span data-stu-id="0acf4-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Dialogové okno VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="0acf4-130">V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.</span><span class="sxs-lookup"><span data-stu-id="0acf4-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="0acf4-131">Do panelu hledání zadejte *ml.NET model Builder* , vyberte ml.NET model Builder (Preview).</span><span class="sxs-lookup"><span data-stu-id="0acf4-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="0acf4-133">Podle pokynů dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="0acf4-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="0acf4-134">Odinstalovat</span><span class="sxs-lookup"><span data-stu-id="0acf4-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="0acf4-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0acf4-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="0acf4-136">Na řádku nabídek vyberte **nástroje** > **rozšíření a aktualizace** .</span><span class="sxs-lookup"><span data-stu-id="0acf4-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="0acf4-138">V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .</span><span class="sxs-lookup"><span data-stu-id="0acf4-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="0acf4-139">V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .</span><span class="sxs-lookup"><span data-stu-id="0acf4-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="0acf4-141">Dokončete odinstalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="0acf4-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="0acf4-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0acf4-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="0acf4-143">Na řádku nabídek vyberte **rozšíření** > **Spravovat rozšíření** .</span><span class="sxs-lookup"><span data-stu-id="0acf4-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="0acf4-145">V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .</span><span class="sxs-lookup"><span data-stu-id="0acf4-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="0acf4-146">V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .</span><span class="sxs-lookup"><span data-stu-id="0acf4-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="0acf4-148">Dokončete odinstalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="0acf4-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="0acf4-149">Upgradovat</span><span class="sxs-lookup"><span data-stu-id="0acf4-149">Upgrade</span></span>

<span data-ttu-id="0acf4-150">Proces upgradu je podobný procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="0acf4-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="0acf4-151">Buď si stáhněte nejnovější verzi z Visual Studio Marketplace nebo použijte Správce rozšíření v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0acf4-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
