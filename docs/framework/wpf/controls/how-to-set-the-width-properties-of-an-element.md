---
title: "Postupy: Nastavení vlastností šířky elementu"
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
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830289f13ac89601f0d3539e2f4400e56a2476f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Postupy: Nastavení vlastností šířky elementu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vizuálně rozdíly v chování mezi čtyři vlastnosti související s šířka v vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Třída zpřístupňuje čtyři vlastnosti, které popisují charakteristiky šířka elementu. Tyto čtyři vlastnosti může dojít ke konfliktu, a pokud tomu tak je, hodnotu, která má přednost před se určuje takto: <xref:System.Windows.FrameworkElement.MinWidth%2A> hodnota má přednost před <xref:System.Windows.FrameworkElement.MaxWidth%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Width%2A> hodnotu. Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualWidth%2A>, je jen pro čtení a skutečná šířka určeného interakce s proces rozložení sestavy.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady kreslení <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený <xref:System.Windows.Controls.Canvas>. Můžete změnit vlastnosti šířku <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, a <xref:System.Windows.FrameworkElement.Width%2A>. Tímto způsobem se zobrazí vizuálně prioritu každé vlastnosti.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Následující příklady kódu zpracování události, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolá událost. Každá vlastní metoda přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadané vlastnosti související s šířku. Šířka hodnoty jsou také převedeno na řetězec a zapisovat do různých <xref:System.Windows.Controls.TextBlock> elementy (definice těchto elementů není znázorněné vybrané XAML).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Kompletní příklad, najdete v části [šířka vlastnosti porovnání ukázka](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Nastavte vlastnosti Výška elementu](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [Ukázka porovnání vlastnosti Šířka](http://go.microsoft.com/fwlink/?LinkID=160050)
