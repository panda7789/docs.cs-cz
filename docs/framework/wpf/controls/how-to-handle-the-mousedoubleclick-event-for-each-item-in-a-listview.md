---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460227"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="af9c6-102">Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView</span><span class="sxs-lookup"><span data-stu-id="af9c6-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="af9c6-103">Chcete-li zpracovat událost pro položku v <xref:System.Windows.Controls.ListView>, je nutné přidat obslužnou rutinu události do každého <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="af9c6-104">Pokud je <xref:System.Windows.Controls.ListView> svázán se zdrojem dat, nevytvoříte explicitně <xref:System.Windows.Controls.ListViewItem>, ale můžete zpracovat událost pro každou položku přidáním <xref:System.Windows.EventSetter> do stylu <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af9c6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="af9c6-105">Example</span></span>  
 <span data-ttu-id="af9c6-106">Následující příklad vytvoří datově vázaný <xref:System.Windows.Controls.ListView> a vytvoří <xref:System.Windows.Style> pro přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="af9c6-107">Následující příklad zpracovává událost <xref:System.Windows.Controls.Control.MouseDoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="af9c6-108">I když je nejběžnější vytvořit vazbu <xref:System.Windows.Controls.ListView> ke zdroji dat, můžete použít styl k přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem> v nevázané <xref:System.Windows.Controls.ListView> dat bez ohledu na to, zda explicitně vytvoříte <xref:System.Windows.Controls.ListViewItem>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="af9c6-109">Další informace o explicitním a implicitně vytvořeném ovládacím prvku <xref:System.Windows.Controls.ListViewItem> naleznete v tématu <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="af9c6-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9c6-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af9c6-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="af9c6-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="af9c6-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="af9c6-112">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="af9c6-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="af9c6-113">Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath</span><span class="sxs-lookup"><span data-stu-id="af9c6-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="af9c6-114">ListView – přehled</span><span class="sxs-lookup"><span data-stu-id="af9c6-114">ListView Overview</span></span>](listview-overview.md)
