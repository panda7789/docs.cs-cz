---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646114"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="c45d9-102">Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView</span><span class="sxs-lookup"><span data-stu-id="c45d9-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="c45d9-103">Chcete-li zpracovat událost <xref:System.Windows.Controls.ListView>pro položku v aplikaci <xref:System.Windows.Controls.ListViewItem>, je třeba ke každé události přidat obslužnou rutinu .</span><span class="sxs-lookup"><span data-stu-id="c45d9-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="c45d9-104">Pokud <xref:System.Windows.Controls.ListView> je a vázána na zdroj dat, <xref:System.Windows.Controls.ListViewItem>není explicitně vytvořit , ale můžete <xref:System.Windows.EventSetter> zpracovat událost <xref:System.Windows.Controls.ListViewItem>pro každou položku přidáním styl .</span><span class="sxs-lookup"><span data-stu-id="c45d9-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c45d9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c45d9-105">Example</span></span>  
 <span data-ttu-id="c45d9-106">Následující příklad vytvoří vazbu <xref:System.Windows.Controls.ListView> na <xref:System.Windows.Style> data a vytvoří pro <xref:System.Windows.Controls.ListViewItem>přidání obslužné rutiny události do každé z nich .</span><span class="sxs-lookup"><span data-stu-id="c45d9-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="c45d9-107">Následující příklad zpracovává <xref:System.Windows.Controls.Control.MouseDoubleClick> událost.</span><span class="sxs-lookup"><span data-stu-id="c45d9-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="c45d9-108">Přestože <xref:System.Windows.Controls.ListView> je nejběžnější svázat a se zdrojem dat, můžete použít styl <xref:System.Windows.Controls.ListViewItem> přidat obslužnou rutinu události do každého v non-data-bound <xref:System.Windows.Controls.ListView> bez ohledu na to, zda explicitně vytvořit <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="c45d9-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="c45d9-109">Další informace o explicitně <xref:System.Windows.Controls.ListViewItem> a implicitně vytvořených ovládacích prvcích naleznete v tématu <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="c45d9-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45d9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c45d9-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="c45d9-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c45d9-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c45d9-112">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c45d9-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c45d9-113">Vazba na data XML pomocí dotazů XMLDataProvider a XPath</span><span class="sxs-lookup"><span data-stu-id="c45d9-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="c45d9-114">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="c45d9-114">ListView Overview</span></span>](listview-overview.md)
