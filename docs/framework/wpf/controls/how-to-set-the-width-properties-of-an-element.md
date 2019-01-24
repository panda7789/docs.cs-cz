---
title: 'Postupy: Nastavení vlastností šířky elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 739b041d8ca89abb9bd1934abb997d1154f08c95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673982"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Postupy: Nastavení vlastností šířky elementu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vizuálně rozdíly při vykreslování chování mezi čtyři vlastnosti související s šířku v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Třída zveřejňuje čtyři vlastnosti, které popisují vlastností šířky elementu. Tyto čtyři vlastnosti může dojít ke konfliktu, a kdy to dělají, hodnotu, která má přednost před je stanoven následujícím způsobem: <xref:System.Windows.FrameworkElement.MinWidth%2A> přednost <xref:System.Windows.FrameworkElement.MaxWidth%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Width%2A> hodnotu. Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualWidth%2A>, je jen pro čtení a šířku skutečné určeného interakce s procesem rozložení sestavy.  
  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslit příklady <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený objekt <xref:System.Windows.Controls.Canvas>. Můžete změnit vlastnosti šířku <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, a <xref:System.Windows.FrameworkElement.Width%2A>. Tímto způsobem se zobrazí vizuální prioritu každé vlastnosti.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Následující příklady použití modelu code-behind zpracování událostí, který <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává události. Každá vlastní metoda přijímá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnoty jako <xref:System.Double>a použije hodnotu zadané vlastnosti týkající se šířky. Šířka hodnoty jsou také převést na řetězec a zapsána do různých <xref:System.Windows.Controls.TextBlock> prvky (definice těchto prvků není zobrazené ve vybrané XAML).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Úplnou ukázku najdete v tématu [ukázkové porovnání vlastnosti Šířka](https://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Nastavení vlastností výšky elementu](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)
- [Ukázkové porovnání vlastnosti šířky](https://go.microsoft.com/fwlink/?LinkID=160050)
