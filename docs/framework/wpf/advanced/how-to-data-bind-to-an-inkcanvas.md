---
title: 'Postupy: Datové připojení k objektu InkCanvas'
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 4081ae7dd6854934804062cfce60d10106c1e1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543167"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Postupy: Datové připojení k objektu InkCanvas
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost <xref:System.Windows.Controls.InkCanvas> do jiného <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnost ke zdroji dat.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Následující příklad uvádí dva <xref:System.Windows.Controls.InkCanvas> objekty v jazyce XAML a vytvoří datová vazba mezi nimi a jiných zdrojů dat.  První <xref:System.Windows.Controls.InkCanvas>, volané `ic`, je vázána na dvou zdrojů dat.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> a <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti `ic` je vázána na <xref:System.Windows.Controls.ListBox> objekty, které jsou naopak vázány na pole definovaná v XAML.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, A <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnosti druhého <xref:System.Windows.Controls.InkCanvas> je vázána na první <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
