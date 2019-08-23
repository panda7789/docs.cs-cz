---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962064"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="bdacf-102">Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView</span><span class="sxs-lookup"><span data-stu-id="bdacf-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="bdacf-103">Chcete-li zpracovat událost pro položku v <xref:System.Windows.Controls.ListView>, je nutné přidat obslužnou rutinu <xref:System.Windows.Controls.ListViewItem>události.</span><span class="sxs-lookup"><span data-stu-id="bdacf-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="bdacf-104">Je- <xref:System.Windows.Controls.ListView> li objekt svázán se zdrojem dat, <xref:System.Windows.Controls.ListViewItem>nevytvoříte explicitně, ale můžete zpracovat událost pro <xref:System.Windows.EventSetter> každou položku přidáním do stylu <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="bdacf-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdacf-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdacf-105">Example</span></span>  
 <span data-ttu-id="bdacf-106">Následující příklad vytvoří datovou vazbu <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Style> vytvoří pro přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="bdacf-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="bdacf-107">Následující příklad zpracovává <xref:System.Windows.Controls.Control.MouseDoubleClick> událost.</span><span class="sxs-lookup"><span data-stu-id="bdacf-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="bdacf-108">I když je <xref:System.Windows.Controls.ListView> nejběžnější vytvořit vazbu na zdroj dat, můžete použít styl k přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem> nevázaného <xref:System.Windows.Controls.ListView> data <xref:System.Windows.Controls.ListViewItem>bez ohledu na to, zda explicitně vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="bdacf-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="bdacf-109">Další informace o explicitních a implicitně vytvořených <xref:System.Windows.Controls.ListViewItem> ovládacích prvcích naleznete <xref:System.Windows.Controls.ItemsControl>v tématu.</span><span class="sxs-lookup"><span data-stu-id="bdacf-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdacf-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdacf-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="bdacf-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="bdacf-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="bdacf-112">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="bdacf-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="bdacf-113">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="bdacf-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="bdacf-114">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="bdacf-114">ListView Overview</span></span>](listview-overview.md)
