---
title: 'Postupy: Použití vlastnosti BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
