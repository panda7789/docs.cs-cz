---
title: 'Postupy: Změna velikosti sloupců pomocí objektu GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
ms.openlocfilehash: 6bf09c41145aca8690fe3e80fd76a7a859713ad6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562138"
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Postupy: Změna velikosti sloupců pomocí objektu GridSplitter
Tento příklad ukazuje, jak vytvořit a jsou odděleny svislou <xref:System.Windows.Controls.GridSplitter> aby bylo možné znovu distribuovat mezeru mezi dva sloupce <xref:System.Windows.Controls.Grid> beze změny velikosti <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Příklad  
 **Vytvoření objektu GridSplitter které překrývá okraj sloupce**  
  
 Chcete-li určit <xref:System.Windows.Controls.GridSplitter> , která přizpůsobí svou velikost sousedící sloupce v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit velikost. Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počtu řádků. Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Left> nebo <xref:System.Windows.HorizontalAlignment.Right> (zarovnání, které nastavíte, závisí na dva sloupce, které chcete změnit velikost). Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> , který nemá vlastní sloupce mohou být skryty ovládací prvky v <xref:System.Windows.Controls.Grid>. Další informace o tom, jak tomuto problému předejít, naleznete v tématu [zkontrolujte, zda je viditelný objektu GridSplitter](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak vytvořit, který bude zabírat sloupec objektu GridSplitter**  
  
 K určení <xref:System.Windows.Controls.GridSplitter> , který bude zabírat sloupec v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit velikost. Pokud vaše mřížka obsahuje více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počtu řádků. Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> k <xref:System.Windows.HorizontalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.ColumnDefinition.Width%2A> sloupce, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.  
  
 Následující příklad ukazuje, jak definovat a jsou odděleny svislou <xref:System.Windows.Controls.GridSplitter> , které zabírá sloupec a změní velikost sloupců na obou stranách.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.GridSplitter>
- [Témata s postupy](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
