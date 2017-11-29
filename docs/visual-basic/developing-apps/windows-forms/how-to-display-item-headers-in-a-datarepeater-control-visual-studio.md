---
title: "Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da02f9374471a581a58131e26d618f91d7cbb7af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="8457a-102">Postupy: Zobrazení položek záhlaví v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8457a-102">How to: Display Item Headers in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="8457a-103">Položka hlavičky v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení poskytuje vizuální indikátor při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> je vybrána.</span><span class="sxs-lookup"><span data-stu-id="8457a-103">The item header in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control provides a visual indicator when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> is selected.</span></span> <span data-ttu-id="8457a-104">Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (výchozí), hlavička se zobrazí vlevo od jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="8457a-104">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (the default), the item header is displayed to the left of each item.</span></span> <span data-ttu-id="8457a-105">Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, hlavička se zobrazí v horní části každé položky.</span><span class="sxs-lookup"><span data-stu-id="8457a-105">When the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, the item header is displayed at the top of each item.</span></span>  
  
 <span data-ttu-id="8457a-106">První vybranou, hlavička se zobrazí v barvu, která je zadána <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> se zobrazí vlastnosti a ikona bílé šipky.</span><span class="sxs-lookup"><span data-stu-id="8457a-106">When it is first selected, the item header is displayed in the color that is specified by the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property, and a white arrow icon is displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8457a-107">Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru nezobrazí první vybranou položku.</span><span class="sxs-lookup"><span data-stu-id="8457a-107">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
 <span data-ttu-id="8457a-108">Když pole v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> má právě fokus, barva změny položky hlavičky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> barvy a změny ikonu šipky černé na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8457a-108">When a field in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> has focus, the color of the item header changes to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> background color and the arrow icon changes to black.</span></span> <span data-ttu-id="8457a-109">Pokud dojde ke změně dat, se zobrazí symbol tužky v hlavičce položky.</span><span class="sxs-lookup"><span data-stu-id="8457a-109">If data is changed, a pencil symbol is displayed in the item header.</span></span>  
  
 <span data-ttu-id="8457a-110">Výchozí šířku (nebo výšky při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) položky hlavičky je 15 pixelů.</span><span class="sxs-lookup"><span data-stu-id="8457a-110">The default width (or height when the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) of the item header is 15 pixels.</span></span> <span data-ttu-id="8457a-111">Můžete změnit šířku nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8457a-111">You can change the width by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8457a-112">Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, symbol indikátoru v hlavičce položky se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="8457a-112">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
 <span data-ttu-id="8457a-113">Záhlaví položek můžete skrýt, a to nastavením <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="8457a-113">You can hide the item headers by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span> <span data-ttu-id="8457a-114">Když <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> je nastaven na **False**, jediné, že je vybrána položka je tečkovaná čára po obvodu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="8457a-114">When <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> is set to **False**, the only indication that an item is selected is a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8457a-115">Můžete také zadat vlastní indikátor výběru sledováním <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> vlastnost <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> události <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8457a-115">You can also provide your own selection indicator by monitoring the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> property of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8457a-116">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span><span class="sxs-lookup"><span data-stu-id="8457a-116">For more information, see <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.</span></span>  
  
### <a name="to-change-the-appearance-of-item-headers"></a><span data-ttu-id="8457a-117">Změna vzhledu položky záhlaví</span><span class="sxs-lookup"><span data-stu-id="8457a-117">To change the appearance of item headers</span></span>  
  
1.  <span data-ttu-id="8457a-118">V Návrháři formulářů Windows, vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8457a-118">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8457a-119">Je třeba vybrat nižší oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8457a-119">You must select the lower region of the control.</span></span> <span data-ttu-id="8457a-120">Pokud vyberete oddíl šablony položky, zobrazí se v okně vlastností jinou sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="8457a-120">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="8457a-121">V okně Vlastnosti použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> vlastnosti chcete změnit barvu položky záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8457a-121">In the Properties window, use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> property to change the color of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8457a-122">Pokud nastavíte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> k <xref:System.Drawing.Color.White%2A>, symbol výběru nezobrazí první vybranou položku.</span><span class="sxs-lookup"><span data-stu-id="8457a-122">If you set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> to <xref:System.Drawing.Color.White%2A>, the selection symbol will not be visible when the item is first selected.</span></span>  
  
3.  <span data-ttu-id="8457a-123">Použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> vlastnost změnit šířku (nebo výška) položek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8457a-123">Use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property to change the width (or height) of the item headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8457a-124">Pokud <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> je nastavena na hodnotu, která je menší než 11, symbol indikátoru v hlavičce položky se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="8457a-124">If the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> property is set to a value that is less than 11, the indicator symbols in the item header will not be displayed.</span></span>  
  
### <a name="to-hide-item-headers"></a><span data-ttu-id="8457a-125">Skrytí položek záhlaví</span><span class="sxs-lookup"><span data-stu-id="8457a-125">To hide item headers</span></span>  
  
1.  <span data-ttu-id="8457a-126">V Návrháři formulářů Windows, vyberte menší oblast <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8457a-126">In the Windows Forms Designer, select the lower region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8457a-127">Je třeba vybrat nižší oblast ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8457a-127">You must select the lower region of the control.</span></span> <span data-ttu-id="8457a-128">Pokud vyberete oddíl šablony položky, zobrazí se v okně vlastností jinou sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="8457a-128">If you select the item template section, a different set of properties will appear in the Properties window.</span></span>  
  
2.  <span data-ttu-id="8457a-129">V okně vlastnosti nastavit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="8457a-129">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> property to **False**.</span></span>  
  
     <span data-ttu-id="8457a-130">Když je položka v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vybrána, bude jediné tečkovaná čára po obvodu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span><span class="sxs-lookup"><span data-stu-id="8457a-130">When an item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is selected, the only indication will be a dotted line around the perimeter of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8457a-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8457a-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="8457a-132">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8457a-132">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8457a-133">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8457a-133">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8457a-134">Postupy: Změna rozložení ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8457a-134">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8457a-135">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8457a-135">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
