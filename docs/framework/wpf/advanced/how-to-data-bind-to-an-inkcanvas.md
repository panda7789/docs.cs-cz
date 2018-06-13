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
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="da429-102">Postupy: Datové připojení k objektu InkCanvas</span><span class="sxs-lookup"><span data-stu-id="da429-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="da429-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="da429-103">Example</span></span>  
 <span data-ttu-id="da429-104">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost <xref:System.Windows.Controls.InkCanvas> do jiného <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="da429-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="da429-105">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnost ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="da429-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="da429-106">Následující příklad uvádí dva <xref:System.Windows.Controls.InkCanvas> objekty v jazyce XAML a vytvoří datová vazba mezi nimi a jiných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="da429-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="da429-107">První <xref:System.Windows.Controls.InkCanvas>, volané `ic`, je vázána na dvou zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="da429-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="da429-108"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A> a <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> vlastnosti `ic` je vázána na <xref:System.Windows.Controls.ListBox> objekty, které jsou naopak vázány na pole definovaná v XAML.</span><span class="sxs-lookup"><span data-stu-id="da429-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="da429-109"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, A <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnosti druhého <xref:System.Windows.Controls.InkCanvas> je vázána na první <xref:System.Windows.Controls.InkCanvas>, `ic`.</span><span class="sxs-lookup"><span data-stu-id="da429-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
