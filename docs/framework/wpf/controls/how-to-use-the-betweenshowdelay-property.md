---
title: 'Postupy: Používání vlastnosti BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 9b63675ec21294496117860aa5b58af132c4284a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614531"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Postupy: Používání vlastnosti BetweenShowDelay
Tento příklad ukazuje způsob použití <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> čas vlastnost tak, aby popisky zobrazeny rychle – žádné nebo téměř žádné zpoždění – když uživatel přesune ukazatel myši z jeden popis přímo do jiného.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> je nastavena na jedné sekundě (1000 milisekund) a <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> nastavena na 2 sekundy (2000 MS) pro popisky obou <xref:System.Windows.Shapes.Ellipse> ovládacích prvků. Je-li zobrazit v popisu pro jeden symbol tří teček a potom přesuňte ukazatel myši na další tři tečky v rámci dvou sekund a pozastavení na něm popisku druhého elipsa zobrazí okamžitě.  
  
 V některém z následujících scénářů <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> vztahuje, což způsobí, že popisek pro druhý elipsa čekat jedné sekundy předtím, než se zobrazí:  
  
- Pokud čas potřebný k přesunutí do druhé tlačítko je více než 2 sekundy.  
  
- Pokud popisek se nezobrazuje na začátku časového intervalu pro první tři tečky.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Témata s postupy](tooltip-how-to-topics.md)
- [ToolTip – přehled](tooltip-overview.md)
