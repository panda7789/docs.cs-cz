---
title: 'Postupy: Vytvoření nového nastavení při návrhu'
description: Naučte se, jak vytvořit nové nastavení model Windows Forms v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325843"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="11f9a-103">Postupy: vytvoření nového nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="11f9a-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="11f9a-104">Nové nastavení můžete vytvořit v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11f9a-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="11f9a-105">Návrhář nastavení je rozhraní ve stylu mřížky, které umožňuje vytvořit nové nastavení a zadat vlastnosti těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="11f9a-106">Pro nová nastavení musíte zadat název, hodnotu, typ a rozsah.</span><span class="sxs-lookup"><span data-stu-id="11f9a-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="11f9a-107">Jakmile je nastavení vytvořeno, je přístupné v kódu.</span><span class="sxs-lookup"><span data-stu-id="11f9a-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="11f9a-108">Vytvořit nové nastavení v době návrhu v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="11f9a-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="11f9a-109">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11f9a-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="11f9a-110">V **Průzkumník řešení**rozbalte uzel **vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="11f9a-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="11f9a-111">Dvakrát klikněte na soubor. Settings, ve kterém chcete přidat nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="11f9a-112">Výchozí název tohoto souboru je Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="11f9a-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="11f9a-113">V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="11f9a-114">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="11f9a-115">Vytvořit nové nastavení v době návrhu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11f9a-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="11f9a-116">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11f9a-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="11f9a-117">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="11f9a-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="11f9a-118">Na stránce **vlastnosti** vyberte kartu **Nastavení** .</span><span class="sxs-lookup"><span data-stu-id="11f9a-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="11f9a-119">V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="11f9a-120">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="11f9a-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="11f9a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="11f9a-121">See also</span></span>

- [<span data-ttu-id="11f9a-122">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="11f9a-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="11f9a-123">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="11f9a-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="11f9a-124">Postupy: Změna hodnoty existujícího nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="11f9a-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
