---
title: 'Postupy: Vytvoření nového nastavení při návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037908"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="8fe77-102">Postupy: Vytvořit nové nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="8fe77-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="8fe77-103">Nové nastavení můžete vytvořit v době návrhu pomocí návrháře nastavení v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8fe77-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="8fe77-104">Návrhář nastavení je rozhraní ve stylu mřížky, které umožňuje vytvořit nové nastavení a zadat vlastnosti těchto nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="8fe77-105">Pro nová nastavení musíte zadat název, hodnotu, typ a rozsah.</span><span class="sxs-lookup"><span data-stu-id="8fe77-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="8fe77-106">Jakmile je nastavení vytvořeno, je přístupné v kódu.</span><span class="sxs-lookup"><span data-stu-id="8fe77-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="8fe77-107">Vytvořit nové nastavení v době návrhu v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="8fe77-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="8fe77-108">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8fe77-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="8fe77-109">V **Průzkumník řešení**rozbalte uzel **vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="8fe77-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="8fe77-110">Dvakrát klikněte na soubor. Settings, ve kterém chcete přidat nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="8fe77-111">Výchozí název tohoto souboru je Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="8fe77-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="8fe77-112">V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="8fe77-113">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="8fe77-114">Vytvořit nové nastavení v době návrhu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fe77-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="8fe77-115">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8fe77-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="8fe77-116">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8fe77-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="8fe77-117">Na stránce **vlastnosti** vyberte kartu **Nastavení** .</span><span class="sxs-lookup"><span data-stu-id="8fe77-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="8fe77-118">V Návrháři nastavení nastavte **název**, **hodnotu**, **typ**a **Rozsah** vašeho nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="8fe77-119">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fe77-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fe77-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe77-120">See also</span></span>

- [<span data-ttu-id="8fe77-121">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="8fe77-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="8fe77-122">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="8fe77-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="8fe77-123">Postupy: Změna hodnoty existujícího nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="8fe77-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
