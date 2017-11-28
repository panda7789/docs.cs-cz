---
title: "Postupy: Použití vlastnosti BetweenShowDelay"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="ca7bf-102">Postupy: Použití vlastnosti BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="ca7bf-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="ca7bf-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> čas vlastnost tak, aby rychle zobrazí popisy tlačítek – s minimální nebo žádnou zpožděním – Pokud uživatel přesune ukazatel myši z jednoho popisku přímo na jiný.</span><span class="sxs-lookup"><span data-stu-id="ca7bf-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7bf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca7bf-104">Example</span></span>  
 <span data-ttu-id="ca7bf-105">V následujícím příkladu <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> je nastavena na jednu sekundu (1000 milisekund) a <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> nastavena na 2 sekundy (2000 v milisekundách) pro popisky tlačítek obou <xref:System.Windows.Shapes.Ellipse> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ca7bf-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="ca7bf-106">Pokud se zobrazí popisek pro jednu z na symbol tří teček a poté přesuňte ukazatel myši do jiné elipsy v rámci dvou sekund a pozastavení na něm, popis druhý elipsy zobrazí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="ca7bf-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="ca7bf-107">V některém z následujících scénářů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vztahuje, což způsobí, že popisek pro druhý elipsy čekání sekundu předtím, než se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="ca7bf-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="ca7bf-108">Pokud čas potřebný pro přesun do druhé tlačítko je více než dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="ca7bf-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="ca7bf-109">Pokud na začátku časový interval pro první elipsy není viditelná z popisu.</span><span class="sxs-lookup"><span data-stu-id="ca7bf-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="ca7bf-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca7bf-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="ca7bf-111">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="ca7bf-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="ca7bf-112">ToolTip – přehled</span><span class="sxs-lookup"><span data-stu-id="ca7bf-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
