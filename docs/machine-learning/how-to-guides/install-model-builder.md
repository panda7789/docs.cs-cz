---
title: Jak nainstalovat Tvůrce modelů
description: Zjistěte, jak nainstalovat nástroj ML.NET model Builder.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774566"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="06d48-103">Postup instalace Tvůrce modelů ML.NET</span><span class="sxs-lookup"><span data-stu-id="06d48-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="06d48-104">Naučte se instalovat tvůrce modelů ML.NET a přidat do aplikací .NET strojové učení.</span><span class="sxs-lookup"><span data-stu-id="06d48-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="06d48-105">Tvůrce modelů je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="06d48-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="06d48-106">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="06d48-106">Pre-requisites</span></span>

- <span data-ttu-id="06d48-107">Visual Studio 2017 verze 15.9.12 nebo novější/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="06d48-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="06d48-108">Sada .NET Core 2,1 nebo novější SDK</span><span class="sxs-lookup"><span data-stu-id="06d48-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="06d48-109">Omezení</span><span class="sxs-lookup"><span data-stu-id="06d48-109">Limitations</span></span>

- <span data-ttu-id="06d48-110">Rozšíření tvůrce modelů ML.NET je aktuálně funguje pouze v sadě Visual Studio ve Windows.</span><span class="sxs-lookup"><span data-stu-id="06d48-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="06d48-111">Školení pro datovou sadu o velikosti 1 GB</span><span class="sxs-lookup"><span data-stu-id="06d48-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="06d48-112">SQL Server má limit 100 000 řádků pro školení</span><span class="sxs-lookup"><span data-stu-id="06d48-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="06d48-113">Microsoft SQL Server Data Tools for Visual Studio 2017 se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="06d48-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="06d48-114">Instalace</span><span class="sxs-lookup"><span data-stu-id="06d48-114">Install</span></span>

<span data-ttu-id="06d48-115">Tvůrce modelů ML.NET se dá nainstalovat buď prostřednictvím Visual Studio Marketplace, nebo v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06d48-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="06d48-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="06d48-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="06d48-117">Stáhnout z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="06d48-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="06d48-118">Podle zobrazených výzev nainstalujte do příslušné verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06d48-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="06d48-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="06d48-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="06d48-120">V řádku nabídek vyberte **nástroje**  > **rozšíření a aktualizace** .</span><span class="sxs-lookup"><span data-stu-id="06d48-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Dialogové okno VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="06d48-122">V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.</span><span class="sxs-lookup"><span data-stu-id="06d48-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="06d48-123">Na panelu hledání vyhledejte *Tvůrce modelů ml.NET* a z výsledků vyberte ml.NET model Builder (Preview).</span><span class="sxs-lookup"><span data-stu-id="06d48-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="06d48-125">Podle pokynů dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="06d48-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="06d48-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="06d48-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="06d48-127">Na řádku nabídek vyberte **rozšíření**  > **Spravovat rozšíření** .</span><span class="sxs-lookup"><span data-stu-id="06d48-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Dialogové okno VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="06d48-129">V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.</span><span class="sxs-lookup"><span data-stu-id="06d48-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="06d48-130">Do panelu hledání zadejte *ml.NET model Builder* , vyberte ml.NET model Builder (Preview).</span><span class="sxs-lookup"><span data-stu-id="06d48-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="06d48-132">Podle pokynů dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="06d48-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="06d48-133">Odinstalovat</span><span class="sxs-lookup"><span data-stu-id="06d48-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="06d48-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="06d48-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="06d48-135">Na řádku nabídek vyberte **nástroje**  > **rozšíření a aktualizace** .</span><span class="sxs-lookup"><span data-stu-id="06d48-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="06d48-137">V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .</span><span class="sxs-lookup"><span data-stu-id="06d48-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="06d48-138">V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .</span><span class="sxs-lookup"><span data-stu-id="06d48-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="06d48-140">Dokončete odinstalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="06d48-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="06d48-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="06d48-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="06d48-142">Na řádku nabídek vyberte **rozšíření**  > **Spravovat rozšíření** .</span><span class="sxs-lookup"><span data-stu-id="06d48-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="06d48-144">V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .</span><span class="sxs-lookup"><span data-stu-id="06d48-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="06d48-145">V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .</span><span class="sxs-lookup"><span data-stu-id="06d48-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="06d48-147">Dokončete odinstalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="06d48-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="06d48-148">Přejít</span><span class="sxs-lookup"><span data-stu-id="06d48-148">Upgrade</span></span>

<span data-ttu-id="06d48-149">Proces upgradu je podobný procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="06d48-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="06d48-150">Buď si stáhněte nejnovější verzi z Visual Studio Marketplace nebo použijte Správce rozšíření v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06d48-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
