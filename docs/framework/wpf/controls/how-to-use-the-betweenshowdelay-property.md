---
title: 'Postupy: Používání vlastnosti BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: b6d55c72c8264546949833fc086937a8b1fe2540
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139591"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="68fe5-102">Postupy: Používání vlastnosti BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="68fe5-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="68fe5-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> čas vlastnost tak, aby popisky zobrazeny rychle – žádné nebo téměř žádné zpoždění – když uživatel přesune ukazatel myši z jeden popis přímo do jiného.</span><span class="sxs-lookup"><span data-stu-id="68fe5-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fe5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="68fe5-104">Example</span></span>  
 <span data-ttu-id="68fe5-105">V následujícím příkladu <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> je nastavena na jedné sekundě (1000 milisekund) a <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> nastavena na 2 sekundy (2000 MS) pro popisky obou <xref:System.Windows.Shapes.Ellipse> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="68fe5-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="68fe5-106">Je-li zobrazit v popisu pro jeden symbol tří teček a potom přesuňte ukazatel myši na další tři tečky v rámci dvou sekund a pozastavení na něm popisku druhého elipsa zobrazí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="68fe5-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="68fe5-107">V některém z následujících scénářů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vztahuje, což způsobí, že popisek pro druhý elipsa čekat jedné sekundy předtím, než se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="68fe5-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="68fe5-108">Pokud čas potřebný k přesunutí do druhé tlačítko je více než 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="68fe5-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="68fe5-109">Pokud popisek se nezobrazuje na začátku časového intervalu pro první tři tečky.</span><span class="sxs-lookup"><span data-stu-id="68fe5-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="68fe5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68fe5-110">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="68fe5-111">– postupy</span><span class="sxs-lookup"><span data-stu-id="68fe5-111">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="68fe5-112">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="68fe5-112">ToolTip Overview</span></span>](tooltip-overview.md)
