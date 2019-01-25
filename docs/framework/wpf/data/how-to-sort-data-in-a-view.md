---
title: 'Postupy: Řazení dat v zobrazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 50e1426f2a220c7d947f7feb9c3ec7e1c4de7643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522671"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="2c03e-102">Postupy: Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="2c03e-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="2c03e-103">Tento příklad popisuje způsob řazení dat v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2c03e-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c03e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c03e-104">Example</span></span>  
 <span data-ttu-id="2c03e-105">Následující příklad vytvoří jednoduchý <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="2c03e-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="2c03e-106"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obslužná rutina události tlačítka obsahuje logiku a řadit položky v <xref:System.Windows.Controls.ListBox> v sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2c03e-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="2c03e-107">Můžete to provést, protože přidávání položek do <xref:System.Windows.Controls.ListBox> tímto způsobem se přidají do <xref:System.Windows.Controls.ItemCollection> z <xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.ItemCollection> je odvozen od <xref:System.Windows.Data.CollectionView> třídy.</span><span class="sxs-lookup"><span data-stu-id="2c03e-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="2c03e-108">Pokud vytváříte vazbu vaše <xref:System.Windows.Controls.ListBox> do kolekce pomocí <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost, stejný postup můžete použít k seřazení.</span><span class="sxs-lookup"><span data-stu-id="2c03e-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="2c03e-109">Za předpokladu, budete mít odkaz na objekt zobrazení, můžete použít stejný postup k řazení obsahu zobrazení jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="2c03e-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="2c03e-110">Příklad toho, jak získat zobrazení, naleznete v tématu [získat výchozí zobrazení datové kolekce](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="2c03e-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="2c03e-111">Další příklad naleznete v tématu [řazení GridView sloupce při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="2c03e-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="2c03e-112">Další informace o zobrazení, naleznete v tématu vazbu na kolekce v [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2c03e-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="2c03e-113">Příklad toho, jak použít logiku řazení v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], naleznete v tématu [řazení a skupiny dat použitím zobrazení v XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="2c03e-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c03e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c03e-114">See also</span></span>
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="2c03e-115">Řazení sloupce GridView při kliknutí na záhlaví</span><span class="sxs-lookup"><span data-stu-id="2c03e-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="2c03e-116">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="2c03e-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2c03e-117">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="2c03e-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="2c03e-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2c03e-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
