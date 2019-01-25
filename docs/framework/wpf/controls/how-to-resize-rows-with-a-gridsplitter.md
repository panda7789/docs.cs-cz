---
title: 'Postupy: Změna velikosti řádků pomocí prvku GridSplitter'
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 93a04ce55a10f54a6770c279f1773491d7aa463f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740135"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Postupy: Změna velikosti řádků pomocí prvku GridSplitter
Tento příklad ukazuje způsob použití vodorovnou <xref:System.Windows.Controls.GridSplitter> distribuovat mezeru mezi dvěma řádky <xref:System.Windows.Controls.Grid> beze změny velikosti <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Příklad  
 **Vytvoření objektu GridSplitter které překrývá okraj řádku**  
  
 K určení <xref:System.Windows.Controls.GridSplitter> , která přizpůsobí svou velikost sousední řádků v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost na jeden z řádků, které chcete změnit velikost. Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> připojené vlastnosti a určit počet sloupců. Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Top> nebo <xref:System.Windows.VerticalAlignment.Bottom> (zarovnání, které nastavíte, závisí na dvou řádků, kterého chcete změnit velikost). Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Následující příklad ukazuje, jak definovat vodorovnou <xref:System.Windows.Controls.GridSplitter> , která přizpůsobí svou velikost sousední řádků.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> nezabírá svůj vlastní řádek mohou být skryty ovládací prvky v <xref:System.Windows.Controls.Grid>. Další informace o tom, jak tomuto problému předejít, naleznete v tématu [zkontrolujte, zda je viditelný objektu GridSplitter](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Jak vytvořit, který bude zabírat řádek objektu GridSplitter**  
  
 K určení <xref:System.Windows.Controls.GridSplitter> , který bude zabírat řádek v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost na jeden z řádků, které chcete změnit velikost. Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> přidružená vlastnost počtu sloupců. Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.RowDefinition.Height%2A> řádku, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.  
  
 Následující příklad ukazuje, jak definovat vodorovnou <xref:System.Windows.Controls.GridSplitter> , které zabírá řádek a změní velikost řádků na obou stranách.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.GridSplitter>
- [Témata s postupy](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
