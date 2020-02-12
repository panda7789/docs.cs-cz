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
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124283"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Postupy: Nastavení vlastností výšky elementu
## <a name="example"></a>Příklad  
 Tento příklad vizuálně znázorňuje rozdíly v chování vykreslování mezi čtyřmi vlastnostmi, které souvisejí se výškou v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Třída <xref:System.Windows.FrameworkElement> zpřístupňuje čtyři vlastnosti, které popisují vlastnosti výšky prvku. Tyto čtyři vlastnosti mohou kolidovat a když jsou, hodnota, která má přednost, je určena následujícím způsobem: hodnota <xref:System.Windows.FrameworkElement.MinHeight%2A> má přednost před hodnotou <xref:System.Windows.FrameworkElement.MaxHeight%2A>, která zase má přednost před hodnotou <xref:System.Windows.FrameworkElement.Height%2A>. Čtvrtá vlastnost, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, je jen pro čtení a oznamuje skutečnou výšku určenou pomocí interakcí s procesem rozložení.  
  
 Následující příklady [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslí <xref:System.Windows.Shapes.Rectangle> prvek (`rect1`) jako podřízenou položku <xref:System.Windows.Controls.Canvas>. Vlastnosti výšky <xref:System.Windows.Shapes.Rectangle> můžete změnit pomocí řady <xref:System.Windows.Controls.ListBox> prvků, které reprezentují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>a <xref:System.Windows.FrameworkElement.Height%2A>. Tímto způsobem se vizuálně zobrazí priorita každé vlastnosti.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Následující příklady kódu zpracovávají události, které událost <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává. Každá obslužná rutina přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadanou vlastnost související se výškou. Hodnoty výšky jsou také převedeny na řetězec a zapsány do různých <xref:System.Windows.Controls.TextBlock> prvků (definice těchto elementů se ve vybraném XAML nezobrazuje).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Úplnou ukázku najdete v tématu [Ukázka vlastností height](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [Nastavení vlastností šířky elementu](how-to-set-the-width-properties-of-an-element.md)
- [Přehled panelu](panels-overview.md)
- [Ukázka vlastností výšky](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
