---
title: "Postupy: Změna velikosti sloupců pomocí objektu GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Postupy: Změna velikosti sloupců pomocí objektu GridSplitter
Tento příklad ukazuje postup vytvoření svislého <xref:System.Windows.Controls.GridSplitter> Chcete-li znovu distribuovat mezeru mezi dvěma sloupci v <xref:System.Windows.Controls.Grid> bez změnit rozměry <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Příklad  
 **Postup vytvoření GridSplitter které překrývá okraj sloupce**  
  
 K určení <xref:System.Windows.Controls.GridSplitter> , změní sousedících sloupců v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit. Pokud vaše <xref:System.Windows.Controls.Grid> obsahuje více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počet řádků. Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Left> nebo <xref:System.Windows.HorizontalAlignment.Right> (které zarovnání nastavíte závisí na dva sloupce, které chcete změnit velikost). Nakonec nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> , nemá vlastní sloupec mohou být skryty z jiných ovládacích prvků v <xref:System.Windows.Controls.Grid>. Další informace o tom, aby se tento problém, naleznete v části [zkontrolujte, zda, GridSplitter je viditelný](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Postup vytvoření GridSplitter, který bude zabírat sloupec**  
  
 K určení <xref:System.Windows.Controls.GridSplitter> který zabírá sloupec v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit. Pokud vaše mřížky má více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počet řádků. Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> k <xref:System.Windows.HorizontalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.ColumnDefinition.Width%2A> sloupce, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.  
  
 Následující příklad ukazuje, jak definovat svislé <xref:System.Windows.Controls.GridSplitter> který zabírá sloupec a změní velikost sloupců na obou stranách.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GridSplitter>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
