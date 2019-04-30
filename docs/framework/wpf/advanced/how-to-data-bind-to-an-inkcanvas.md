---
title: 'Postupy: Datová vazba k objektu InkCanvas'
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 5d3fc0ed7b6176d7bc68bf20af42c311b5563908
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776464"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Postupy: Datová vazba k objektu InkCanvas
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost <xref:System.Windows.Controls.InkCanvas> do jiného <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnost ke zdroji dat.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Následující příklad deklaruje dvě <xref:System.Windows.Controls.InkCanvas> objekty v XAML a vytvoří datové vazby mezi nimi a dalších zdrojů.  První <xref:System.Windows.Controls.InkCanvas>, označované jako `ic`, je vázán na dva datové zdroje.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> a <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti `ic` jsou vázány na <xref:System.Windows.Controls.ListBox> objekty, které jsou zase vázány na pole definované v XAML.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, A <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnosti druhého <xref:System.Windows.Controls.InkCanvas> jsou vázány na první <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
