---
title: "Postupy: Změna velikosti řádků pomocí prvku GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Postupy: Změna velikosti řádků pomocí prvku GridSplitter
Tento příklad ukazuje, jak používat vodorovných <xref:System.Windows.Controls.GridSplitter> mezery mezi dva řádky v znovu distribuovat <xref:System.Windows.Controls.Grid> bez změnit rozměry <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Příklad  
 **Postup vytvoření GridSplitter které překrývá okraj řádku**  
  
 Chcete-li určit <xref:System.Windows.Controls.GridSplitter> , změní sousedících řádků v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost do jednoho z řádků, které chcete změnit velikost. Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> připojené vlastnosti a určit počet sloupců. Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Top> nebo <xref:System.Windows.VerticalAlignment.Bottom> (které zarovnání nastavíte závisí na dva řádky, které chcete změnit velikost). Nakonec nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 Následující příklad ukazuje, jak definovat vodorovných <xref:System.Windows.Controls.GridSplitter> , změní sousedících řádků.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> nezabírá svůj vlastní řádek mohou být skryty z jiných ovládacích prvků v <xref:System.Windows.Controls.Grid>. Další informace o tom, aby se tento problém, naleznete v části [zkontrolujte, zda, GridSplitter je viditelný](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Postup vytvoření GridSplitter, který bude zabírat řádek**  
  
 Chcete-li určit <xref:System.Windows.Controls.GridSplitter> která sídlí v řádku v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost do jednoho z řádků, které chcete změnit velikost. Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> přidružená vlastnost počet sloupců. Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.RowDefinition.Height%2A> řádku, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.  
  
 Následující příklad ukazuje, jak definovat vodorovných <xref:System.Windows.Controls.GridSplitter> který zabírá jeden řádek a změní velikost řádků na obou stranách.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GridSplitter>  
 [Témata s postupy](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
