---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: f9a1e91051a7f86bf78cb08a3d58e57541ae4987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553844"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="b5a84-102">Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView</span><span class="sxs-lookup"><span data-stu-id="b5a84-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="b5a84-103">Zpracovat událost pro položku v <xref:System.Windows.Controls.ListView>, je nutné přidat obslužné rutiny události pro každé <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="b5a84-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="b5a84-104">Při <xref:System.Windows.Controls.ListView> je vázán ke zdroji dat nevytvoříte explicitně <xref:System.Windows.Controls.ListViewItem>, ale můžete zpracovat událost pro každou položku přidáním <xref:System.Windows.EventSetter> na styl <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="b5a84-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a84-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5a84-105">Example</span></span>  
 <span data-ttu-id="b5a84-106">Následující příklad vytvoří vázané na data <xref:System.Windows.Controls.ListView> a vytvoří <xref:System.Windows.Style> přidání obslužné rutiny události pro každé <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="b5a84-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="b5a84-107">Následující příklad popisovače <xref:System.Windows.Controls.Control.MouseDoubleClick> událostí.</span><span class="sxs-lookup"><span data-stu-id="b5a84-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="b5a84-108">I když se nejčastěji vytvořit vazbu <xref:System.Windows.Controls.ListView> ke zdroji dat můžete použít styl přidání obslužné rutiny události pro každé <xref:System.Windows.Controls.ListViewItem> v jiný vázané na data <xref:System.Windows.Controls.ListView> bez ohledu na to, jestli je explicitně vytvořit <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="b5a84-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="b5a84-109">Další informace o explicitní a implicitní vytvoření <xref:System.Windows.Controls.ListViewItem> najdete v části ovládací prvky, <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="b5a84-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a84-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5a84-110">See Also</span></span>  
 <xref:System.Xml.XmlElement>  
 [<span data-ttu-id="b5a84-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="b5a84-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b5a84-112">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="b5a84-112">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b5a84-113">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="b5a84-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [<span data-ttu-id="b5a84-114">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="b5a84-114">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
