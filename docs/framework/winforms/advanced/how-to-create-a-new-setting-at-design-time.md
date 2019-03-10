---
title: 'Postupy: Vytvořit nové nastavení v době návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 54f64de8cdd47b7fd451d266cca3b7577e9e1d78
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702773"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="40c3d-102">Postupy: Vytvořit nové nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="40c3d-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="40c3d-103">Můžete vytvořit nové nastavení v době návrhu pomocí Návrháře nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="40c3d-104">Návrhář nastavení je styl mřížky rozhraní, které vám umožní vytvořit nové nastavení a zadejte vlastnosti pro tato nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="40c3d-105">Musíte zadat název, hodnotu, typu a rozsahu pro nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="40c3d-106">Po vytvoření nastavení, je dostupná v kódu.</span><span class="sxs-lookup"><span data-stu-id="40c3d-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="40c3d-107">Chcete-li vytvořit nové nastavení v době návrhu v C\#</span><span class="sxs-lookup"><span data-stu-id="40c3d-107">To create a new setting at design time in C\#</span></span>
  
1.  <span data-ttu-id="40c3d-108">V **Průzkumníka řešení**, rozbalte **vlastnosti** uzlu projektu.</span><span class="sxs-lookup"><span data-stu-id="40c3d-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="40c3d-109">Poklikejte na soubor .settings, ve které chcete přidat nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="40c3d-110">Výchozí název pro tento soubor je Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="40c3d-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="40c3d-111">V Návrháři nastavení nastavte název, hodnota, typ a obor pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="40c3d-112">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="40c3d-113">Chcete-li vytvořit nové nastavení v době návrhu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40c3d-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="40c3d-114">V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="40c3d-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="40c3d-115">V **vlastnosti** stránky, vyberte **nastavení** kartu.</span><span class="sxs-lookup"><span data-stu-id="40c3d-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="40c3d-116">V Návrháři nastavení nastavte název, hodnota, typ a obor pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="40c3d-117">Každý řádek představuje jedno nastavení.</span><span class="sxs-lookup"><span data-stu-id="40c3d-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c3d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40c3d-118">See also</span></span>
- [<span data-ttu-id="40c3d-119">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="40c3d-119">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="40c3d-120">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="40c3d-120">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="40c3d-121">Postupy: Změna hodnoty existujícího nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="40c3d-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
