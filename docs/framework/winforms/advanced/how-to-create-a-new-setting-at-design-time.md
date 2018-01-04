---
title: "Postupy: Vytvoření nového nastavení při návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04b86579f45c5a357f8759bf36ae41f7a5c6e98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="66241-102">Postupy: Vytvoření nového nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="66241-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="66241-103">Můžete vytvořit nové nastavení v době návrhu pomocí Návrháře nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="66241-104">Návrhář nastavení je rozhraní stylu mřížky, které vám umožní vytvořit nové nastavení a zadejte vlastnosti pro toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="66241-105">Musíte zadat název, hodnotu, typ a obor pro nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="66241-106">Po vytvoření nastavení je dostupné v kódu.</span><span class="sxs-lookup"><span data-stu-id="66241-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="66241-107">Chcete-li vytvořit nové nastavení v době návrhu v C#</span><span class="sxs-lookup"><span data-stu-id="66241-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="66241-108">V **Průzkumníku řešení**, rozbalte **vlastnosti** uzlu projektu.</span><span class="sxs-lookup"><span data-stu-id="66241-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="66241-109">Poklikejte na soubor .settings, ve které chcete přidat nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="66241-110">Výchozí název pro tento soubor je Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="66241-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="66241-111">V Návrháři nastavení nastavte název, hodnotu, typ a obor pro vaše nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="66241-112">Každý řádek představuje jeden nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="66241-113">Chcete-li vytvořit nové nastavení v době návrhu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66241-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="66241-114">V **Průzkumníku řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="66241-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="66241-115">V **vlastnosti** vyberte **nastavení** kartě.</span><span class="sxs-lookup"><span data-stu-id="66241-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="66241-116">V Návrháři nastavení nastavte název, hodnotu, typ a obor pro vaše nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="66241-117">Každý řádek představuje jeden nastavení.</span><span class="sxs-lookup"><span data-stu-id="66241-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66241-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="66241-118">See Also</span></span>  
 [<span data-ttu-id="66241-119">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="66241-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="66241-120">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="66241-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="66241-121">Postupy: Změna hodnoty existujícího nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="66241-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
