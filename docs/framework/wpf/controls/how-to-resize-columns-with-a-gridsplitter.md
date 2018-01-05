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
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="af17c-102">Postupy: Změna velikosti sloupců pomocí objektu GridSplitter</span><span class="sxs-lookup"><span data-stu-id="af17c-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="af17c-103">Tento příklad ukazuje postup vytvoření svislého <xref:System.Windows.Controls.GridSplitter> Chcete-li znovu distribuovat mezeru mezi dvěma sloupci v <xref:System.Windows.Controls.Grid> bez změnit rozměry <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="af17c-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af17c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="af17c-104">Example</span></span>  
 <span data-ttu-id="af17c-105">**Postup vytvoření GridSplitter které překrývá okraj sloupce**</span><span class="sxs-lookup"><span data-stu-id="af17c-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="af17c-106">K určení <xref:System.Windows.Controls.GridSplitter> , změní sousedících sloupců v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="af17c-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="af17c-107">Pokud vaše <xref:System.Windows.Controls.Grid> obsahuje více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počet řádků.</span><span class="sxs-lookup"><span data-stu-id="af17c-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="af17c-108">Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost <xref:System.Windows.HorizontalAlignment.Left> nebo <xref:System.Windows.HorizontalAlignment.Right> (které zarovnání nastavíte závisí na dva sloupce, které chcete změnit velikost).</span><span class="sxs-lookup"><span data-stu-id="af17c-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="af17c-109">Nakonec nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="af17c-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="af17c-110">A <xref:System.Windows.Controls.GridSplitter> , nemá vlastní sloupec mohou být skryty z jiných ovládacích prvků v <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="af17c-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="af17c-111">Další informace o tom, aby se tento problém, naleznete v části [zkontrolujte, zda, GridSplitter je viditelný](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="af17c-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="af17c-112">**Postup vytvoření GridSplitter, který bude zabírat sloupec**</span><span class="sxs-lookup"><span data-stu-id="af17c-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="af17c-113">K určení <xref:System.Windows.Controls.GridSplitter> který zabírá sloupec v <xref:System.Windows.Controls.Grid>, nastavte <xref:System.Windows.Controls.Grid.Column%2A> přidružená vlastnost pro některý ze sloupců, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="af17c-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="af17c-114">Pokud vaše mřížky má více než jeden řádek, nastavte <xref:System.Windows.Controls.Grid.RowSpan%2A> přidružená vlastnost počet řádků.</span><span class="sxs-lookup"><span data-stu-id="af17c-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="af17c-115">Nastavte <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> k <xref:System.Windows.HorizontalAlignment.Center>, nastavte <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnost <xref:System.Windows.VerticalAlignment.Stretch>a nastavte <xref:System.Windows.Controls.ColumnDefinition.Width%2A> sloupce, který obsahuje <xref:System.Windows.Controls.GridSplitter> k <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="af17c-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="af17c-116">Následující příklad ukazuje, jak definovat svislé <xref:System.Windows.Controls.GridSplitter> který zabírá sloupec a změní velikost sloupců na obou stranách.</span><span class="sxs-lookup"><span data-stu-id="af17c-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="af17c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="af17c-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="af17c-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="af17c-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
