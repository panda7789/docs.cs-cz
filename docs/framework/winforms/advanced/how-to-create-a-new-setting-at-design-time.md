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
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="2de2a-102">Postupy: Vytvoření nového nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="2de2a-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="2de2a-103">Můžete vytvořit nové nastavení v době návrhu pomocí Návrháře nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="2de2a-104">Návrhář nastavení je rozhraní stylu mřížky, které vám umožní vytvořit nové nastavení a zadejte vlastnosti pro toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="2de2a-105">Musíte zadat název, hodnotu, typ a obor pro nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="2de2a-106">Po vytvoření nastavení je dostupné v kódu.</span><span class="sxs-lookup"><span data-stu-id="2de2a-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="2de2a-107">Chcete-li vytvořit nové nastavení v době návrhu v C#</span><span class="sxs-lookup"><span data-stu-id="2de2a-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="2de2a-108">V **Průzkumníku řešení**, rozbalte **vlastnosti** uzlu projektu.</span><span class="sxs-lookup"><span data-stu-id="2de2a-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="2de2a-109">Poklikejte na soubor .settings, ve které chcete přidat nové nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="2de2a-110">Výchozí název pro tento soubor je Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="2de2a-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="2de2a-111">V Návrháři nastavení nastavte název, hodnotu, typ a obor pro vaše nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="2de2a-112">Každý řádek představuje jeden nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="2de2a-113">Chcete-li vytvořit nové nastavení v době návrhu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2de2a-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="2de2a-114">V **Průzkumníku řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2de2a-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="2de2a-115">V **vlastnosti** vyberte **nastavení** kartě.</span><span class="sxs-lookup"><span data-stu-id="2de2a-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="2de2a-116">V Návrháři nastavení nastavte název, hodnotu, typ a obor pro vaše nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="2de2a-117">Každý řádek představuje jeden nastavení.</span><span class="sxs-lookup"><span data-stu-id="2de2a-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de2a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2de2a-118">See Also</span></span>  
 [<span data-ttu-id="2de2a-119">Použití nastavení aplikace a nastavení uživatele</span><span class="sxs-lookup"><span data-stu-id="2de2a-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="2de2a-120">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2de2a-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="2de2a-121">Postupy: Změna hodnoty existujícího nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="2de2a-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
