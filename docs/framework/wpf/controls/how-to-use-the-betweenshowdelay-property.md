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
ms.workload: dotnet
ms.openlocfilehash: dfd4bb4c9e26361e5b8f573d06449b090497acd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Postupy: Použití vlastnosti BetweenShowDelay
Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> čas vlastnost tak, aby rychle zobrazí popisy tlačítek – s minimální nebo žádnou zpožděním – Pokud uživatel přesune ukazatel myši z jednoho popisku přímo na jiný.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> je nastavena na jednu sekundu (1000 milisekund) a <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> nastavena na 2 sekundy (2000 v milisekundách) pro popisky tlačítek obou <xref:System.Windows.Shapes.Ellipse> ovládací prvky. Pokud se zobrazí popisek pro jednu z na symbol tří teček a poté přesuňte ukazatel myši do jiné elipsy v rámci dvou sekund a pozastavení na něm, popis druhý elipsy zobrazí okamžitě.  
  
 V některém z následujících scénářů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vztahuje, což způsobí, že popisek pro druhý elipsy čekání sekundu předtím, než se zobrazí:  
  
-   Pokud čas potřebný pro přesun do druhé tlačítko je více než dvě sekundy.  
  
-   Pokud na začátku časový interval pro první elipsy není viditelná z popisu.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [ToolTip – přehled](../../../../docs/framework/wpf/controls/tooltip-overview.md)
