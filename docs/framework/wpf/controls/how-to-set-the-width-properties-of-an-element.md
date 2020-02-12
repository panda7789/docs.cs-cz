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
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124270"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Postupy: Nastavení vlastností šířky elementu
## <a name="example"></a>Příklad  
 Tento příklad vizuálně znázorňuje rozdíly v chování vykreslování ze čtyř vlastností souvisejících s šířkou v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Třída <xref:System.Windows.FrameworkElement> zpřístupňuje čtyři vlastnosti, které popisují charakteristiky šířky elementu. Tyto čtyři vlastnosti mohou kolidovat a když jsou, hodnota, která má přednost, je určena následujícím způsobem: hodnota <xref:System.Windows.FrameworkElement.MinWidth%2A> má přednost před hodnotou <xref:System.Windows.FrameworkElement.MaxWidth%2A>, která zase má přednost před hodnotou <xref:System.Windows.FrameworkElement.Width%2A>. Čtvrtá vlastnost, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, je jen pro čtení a oznamuje skutečnou šířku určenou v interakcích s procesem rozložení.  
  
 Následující příklady [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslí <xref:System.Windows.Shapes.Rectangle> prvek (`rect1`) jako podřízenou položku <xref:System.Windows.Controls.Canvas>. Vlastnosti šířky <xref:System.Windows.Shapes.Rectangle> lze změnit pomocí řady <xref:System.Windows.Controls.ListBox> prvků, které reprezentují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>a <xref:System.Windows.FrameworkElement.Width%2A>. Tímto způsobem se vizuálně zobrazí priorita každé vlastnosti.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Následující příklady kódu zpracovávají události, které událost <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává. Každá vlastní metoda přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadanou vlastnost související s šířkou. Hodnoty šířky jsou také převedeny na řetězec a zapsány do různých <xref:System.Windows.Controls.TextBlock> prvků (definice těchto elementů se ve vybraném XAML nezobrazuje).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Úplnou ukázku najdete v tématu [porovnání vlastností šířky – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [Přehled panelu](panels-overview.md)
- [Nastavení vlastností výšky elementu](how-to-set-the-height-properties-of-an-element.md)
- [Ukázka porovnání vlastností šířky](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
