---
title: "Postupy: Nastavení vlastností výšky elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc06eea281f7761abfae74edf1547fc914b5655a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Postupy: Nastavení vlastností výšky elementu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vizuálně rozdíly v chování mezi čtyři vlastnosti související s výška v vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Třída zpřístupňuje čtyři vlastnosti, které popisují charakteristiky Výška elementu. Tyto čtyři vlastnosti může dojít ke konfliktu, a pokud tomu tak je, hodnotu, která má přednost před se určuje takto: <xref:System.Windows.FrameworkElement.MinHeight%2A> hodnota má přednost před <xref:System.Windows.FrameworkElement.MaxHeight%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Height%2A> hodnotu. Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualHeight%2A>, je jen pro čtení a výšce skutečné určeného interakce s proces rozložení sestavy.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady kreslení <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený <xref:System.Windows.Controls.Canvas>. Můžete změnit vlastnosti výšky <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.FrameworkElement.Height%2A>. Tímto způsobem se zobrazí vizuálně prioritu každé vlastnosti.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Následující příklady kódu zpracování události, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolá událost. Každou rutinu přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadané vlastnosti související s výšku. Výška hodnoty jsou také převedeno na řetězec a zapisovat do různých <xref:System.Windows.Controls.TextBlock> elementy (definice těchto elementů není znázorněné vybrané XAML).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Kompletní příklad, najdete v části [výška vlastnosti vzorku](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Nastavení vlastností šířky elementu](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Výška vlastnosti vzorku](http://go.microsoft.com/fwlink/?LinkID=159993)
