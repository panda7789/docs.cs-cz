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
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="a226f-102">Postupy: Změna velikosti řádků pomocí prvku GridSplitter</span><span class="sxs-lookup"><span data-stu-id="a226f-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="a226f-103">Tento příklad ukazuje, jak používat vodorovných <xref:System.Windows.Controls.GridSplitter> mezery mezi dva řádky v znovu distribuovat <xref:System.Windows.Controls.Grid> bez změnit rozměry <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="a226f-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a226f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a226f-104">Example</span></span>  
 <span data-ttu-id="a226f-105">**Postup vytvoření GridSplitter které překrývá okraj řádku**</span><span class="sxs-lookup"><span data-stu-id="a226f-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="a226f-106">Chcete-li určit <xref:System.Windows.Controls.GridSplitter> , změní sousedících řádků v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost do jednoho z řádků, které chcete změnit velikost.</span><span class="sxs-lookup"><span data-stu-id="a226f-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="a226f-107">Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> připojené vlastnosti a určit počet sloupců.</span><span class="sxs-lookup"><span data-stu-id="a226f-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="a226f-108">Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Top> nebo <xref:System.Windows.VerticalAlignment.Bottom> (které zarovnání nastavíte závisí na dva řádky, které chcete změnit velikost).</span><span class="sxs-lookup"><span data-stu-id="a226f-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="a226f-109">Nakonec nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="a226f-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="a226f-110">Následující příklad ukazuje, jak definovat vodorovných <xref:System.Windows.Controls.GridSplitter> , změní sousedících řádků.</span><span class="sxs-lookup"><span data-stu-id="a226f-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="a226f-111">A <xref:System.Windows.Controls.GridSplitter> nezabírá svůj vlastní řádek mohou být skryty z jiných ovládacích prvků v <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="a226f-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a226f-112">Další informace o tom, aby se tento problém, naleznete v části [zkontrolujte, zda, GridSplitter je viditelný](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="a226f-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="a226f-113">**Postup vytvoření GridSplitter, který bude zabírat řádek**</span><span class="sxs-lookup"><span data-stu-id="a226f-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="a226f-114">Chcete-li určit <xref:System.Windows.Controls.GridSplitter> která sídlí v řádku v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Row%2A> přidružená vlastnost do jednoho z řádků, které chcete změnit velikost.</span><span class="sxs-lookup"><span data-stu-id="a226f-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="a226f-115">Pokud vaše <xref:System.Windows.Controls.Grid> má více než jeden sloupec, nastavte <xref:System.Windows.Controls.Grid.ColumnSpan%2A> přidružená vlastnost počet sloupců.</span><span class="sxs-lookup"><span data-stu-id="a226f-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="a226f-116">Nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> k <xref:System.Windows.VerticalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.RowDefinition.Height%2A> řádku, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="a226f-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="a226f-117">Následující příklad ukazuje, jak definovat vodorovných <xref:System.Windows.Controls.GridSplitter> který zabírá jeden řádek a změní velikost řádků na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="a226f-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="a226f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a226f-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="a226f-119">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="a226f-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
