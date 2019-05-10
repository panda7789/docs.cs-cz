---
title: 'Postupy: Použití transformace na element při výskytu události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 8f04db274432c0e89c6839bef825976c8a2f853c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630754"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Postupy: Použití transformace na element při výskytu události
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ScaleTransform> při výskytu události. Pojem, který je znázorněna zde je stejný, který používáte pro použití jiné typy transformací. Další informace o dostupných typech transformace, najdete v článku <xref:System.Windows.Media.Transform> třídy nebo [transformuje přehled](transforms-overview.md).  
  
 Použití transformace na element v některém z těchto způsobů:  
  
- Pokud tak učiníte *není* má transformaci, která ovlivňují rozložení, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.  
  
- Pokud chcete transformací, která má být ovlivněn rozložení, použijte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost elementu.  
  
 Následující příklad se vztahuje <xref:System.Windows.Media.ScaleTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tlačítka. Když se ukazatel myši přesune na tlačítko <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti <xref:System.Windows.Media.ScaleTransform> jsou nastaveny na `2`, což způsobí, že tlačítko větší. Pokud ukazatel myši pohybuje, vypnutí tlačítka, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> jsou nastaveny na `1`, což způsobí, že tlačítko vrátit na původní velikost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
- [Přehled směrovaných událostí](../advanced/routed-events-overview.md)
