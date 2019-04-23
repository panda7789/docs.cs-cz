---
title: 'Postupy: Nastavení vlastností výšky elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: fb655630336c3b69afdc726a2e3c5a2cb8838667
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221584"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Postupy: Nastavení vlastností výšky elementu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vizuálně rozdíly v chování mezi čtyři vlastnosti související s výšku ve vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Třída zveřejňuje čtyři vlastnosti, které popisují vlastností výšky elementu. Tyto čtyři vlastnosti může dojít ke konfliktu, a kdy to dělají, hodnotu, která má přednost před je stanoven následujícím způsobem: <xref:System.Windows.FrameworkElement.MinHeight%2A> přednost <xref:System.Windows.FrameworkElement.MaxHeight%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Height%2A> hodnotu. Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualHeight%2A>, která je jen pro čtení a skutečné výška určeného interakce s procesem rozložení sestavy.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslit příklady <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený objekt <xref:System.Windows.Controls.Canvas>. Můžete změnit vlastností výšky <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.FrameworkElement.Height%2A>. Tímto způsobem se zobrazí vizuální prioritu každé vlastnosti.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Následující příklady použití modelu code-behind zpracování událostí, který <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává události. Každý popisovač přijímá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnoty jako <xref:System.Double>a použije hodnotu zadané vlastnosti související s výšku. Výška hodnoty jsou také převést na řetězec a zapsána do různých <xref:System.Windows.Controls.TextBlock> prvky (definice těchto prvků není zobrazené ve vybrané XAML).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Úplnou ukázku najdete v tématu [výška vlastnosti vzorku](https://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Nastavení vlastností šířky elementu](how-to-set-the-width-properties-of-an-element.md)
- [Přehled panelu](panels-overview.md)
- [Výška vlastnosti vzorku](https://go.microsoft.com/fwlink/?LinkID=159993)
