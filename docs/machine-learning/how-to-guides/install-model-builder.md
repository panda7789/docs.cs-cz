---
title: Jak nainstalovat Tvůrce modelů
description: Přečtěte si, jak nainstalovat nástroj ML.NET Tvůrce modelů
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848649"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="9ae0a-103">Jak nainstalovat ML.NET Tvůrce modelů</span><span class="sxs-lookup"><span data-stu-id="9ae0a-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="9ae0a-104">Přečtěte si, jak nainstalovat ML.NET Tvůrce modelů a přidat strojové učení do aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="9ae0a-105">Tvůrce modelů je momentálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ae0a-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ae0a-106">Prerequisites</span></span>

- <span data-ttu-id="9ae0a-107">Visual Studio 2017 verze 15.9.12 nebo novější / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9ae0a-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="9ae0a-108">Sada .NET Core 2.1 SDK nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="9ae0a-109">Sada .NET Core 3.0 SDK není aktuálně podporována.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="9ae0a-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="9ae0a-110">Limitations</span></span>

- <span data-ttu-id="9ae0a-111">ML.NET rozšíření Model Builder aktuálně funguje pouze v sadě Visual Studio v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="9ae0a-112">Trénovací datový set limit 1 GB</span><span class="sxs-lookup"><span data-stu-id="9ae0a-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="9ae0a-113">SQL Server má limit 100 tisíc řádků pro školení</span><span class="sxs-lookup"><span data-stu-id="9ae0a-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="9ae0a-114">Datové nástroje serveru Microsoft SQL Server pro Visual Studio 2017 nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="9ae0a-115">Instalace</span><span class="sxs-lookup"><span data-stu-id="9ae0a-115">Install</span></span>

<span data-ttu-id="9ae0a-116">ML.NET model tvůrce lze nainstalovat buď prostřednictvím Webu Visual Studio Marketplace nebo z Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="9ae0a-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="9ae0a-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="9ae0a-118">Stažení z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="9ae0a-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="9ae0a-119">Instalace do příslušné verze sady Visual Studio navazují na výzvy</span><span class="sxs-lookup"><span data-stu-id="9ae0a-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="9ae0a-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9ae0a-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="9ae0a-121">V řádku nabídek vyberte**Rozšíření a aktualizace** **nástrojů.** > </span><span class="sxs-lookup"><span data-stu-id="9ae0a-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Dialogové okno Správce otevřených rozšíření VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="9ae0a-123">Uvnitř výzvy *Rozšíření a Aktualizace* vyberte online uzel. *Online*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="9ae0a-124">Na vyhledávacím panelu vyhledejte *ML.NET Tvůrce modelů* a z výsledků vyberte ML.NET Tvůrce modelů (Preview).</span><span class="sxs-lookup"><span data-stu-id="9ae0a-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 vyhledává a instaluje rozšíření Tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="9ae0a-126">Dokončete instalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="9ae0a-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9ae0a-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="9ae0a-128">Na řádku nabídek vyberte **Rozšíření** > **Spravovat rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="9ae0a-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Dialogové okno Správce otevřených rozšíření VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="9ae0a-130">Uvnitř výzvy *Rozšíření a Aktualizace* vyberte online uzel. *Online*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="9ae0a-131">Zadejte *ML.NET Tvůrce modelů* do vyhledávacího panelu vyberte ML.NET Tvůrce modelů (Náhled)</span><span class="sxs-lookup"><span data-stu-id="9ae0a-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 vyhledává a instaluje rozšíření Tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="9ae0a-133">Dokončete instalaci podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="9ae0a-134">Odinstalace</span><span class="sxs-lookup"><span data-stu-id="9ae0a-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="9ae0a-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9ae0a-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="9ae0a-136">Na řádku nabídek vyberte**Rozšíření a aktualizace** **nástrojů.** > </span><span class="sxs-lookup"><span data-stu-id="9ae0a-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Dialogové okno Otevřít rozšíření v správě VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="9ae0a-138">V rámci výzvy *Rozšíření a Aktualizace* rozbalte *nainstalovaný* uzel a vyberte *Nástroje.*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="9ae0a-139">Vyberte ML.NET Tvůrce modelů (Preview) ze seznamu nástrojů a pak vyberte *Odinstalovat*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 vyhledávání a odinstalovat rozšíření Model Builder v dialogovém okně správce rozšíření](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="9ae0a-141">Podle pokynů dokončete odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="9ae0a-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="9ae0a-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="9ae0a-143">Na řádku nabídek vyberte **Rozšíření** > **Spravovat rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="9ae0a-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Dialogové okno Otevřít rozšíření v Správě VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="9ae0a-145">V rámci výzvy *Rozšíření a Aktualizace* rozbalte *nainstalovaný* uzel a vyberte *Nástroje.*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="9ae0a-146">Vyberte ML.NET Tvůrce modelů (Preview) ze seznamu nástrojů a pak vyberte *Odinstalovat*</span><span class="sxs-lookup"><span data-stu-id="9ae0a-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 vyhledávání a odinstalovat rozšíření Model Builder v dialogovém okně správce rozšíření](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="9ae0a-148">Podle pokynů dokončete odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="9ae0a-149">Upgrade</span><span class="sxs-lookup"><span data-stu-id="9ae0a-149">Upgrade</span></span>

<span data-ttu-id="9ae0a-150">Proces upgradu je podobný procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="9ae0a-151">Stáhněte si nejnovější verzi z webu Visual Studio Marketplace nebo použijte Správce rozšíření v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ae0a-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
