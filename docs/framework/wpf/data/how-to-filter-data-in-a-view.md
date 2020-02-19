---
title: 'Postupy: Filtrování dat v zobrazení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: f15bcfd1e3c4175f8b4b97244f120d5edbdec9b8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453075"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="4569d-102">Postupy: Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="4569d-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="4569d-103">Tento příklad ukazuje, jak filtrovat data v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4569d-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4569d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4569d-104">Example</span></span>  
 <span data-ttu-id="4569d-105">Chcete-li vytvořit filtr, definujte metodu, která poskytuje logiku filtrování.</span><span class="sxs-lookup"><span data-stu-id="4569d-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="4569d-106">Metoda se používá jako zpětné volání a přijímá parametr typu `object`.</span><span class="sxs-lookup"><span data-stu-id="4569d-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="4569d-107">Následující metoda vrátí všechny objekty `Order` s vlastností `filled` nastavenou na hodnotu Ne, vyfiltruje zbytek objektů.</span><span class="sxs-lookup"><span data-stu-id="4569d-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="4569d-108">Pak můžete použít filtr, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4569d-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="4569d-109">V tomto příkladu je `myCollectionView` objektem <xref:System.Windows.Data.ListCollectionView>.</span><span class="sxs-lookup"><span data-stu-id="4569d-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="4569d-110">Chcete-li zrušit filtrování, můžete nastavit vlastnost <xref:System.Windows.Data.CollectionView.Filter%2A> na hodnotu `null`:</span><span class="sxs-lookup"><span data-stu-id="4569d-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="4569d-111">Informace o tom, jak vytvořit nebo získat zobrazení, najdete v tématu [získání výchozího zobrazení sběru dat](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="4569d-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="4569d-112">Úplný příklad najdete v tématu [řazení a filtrování položek v ukázce zobrazení](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).</span><span class="sxs-lookup"><span data-stu-id="4569d-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).</span></span>  
  
 <span data-ttu-id="4569d-113">Pokud objekt zobrazení pochází z <xref:System.Windows.Data.CollectionViewSource> objektu, použijete logiku filtrování nastavením obslužné rutiny události pro událost <xref:System.Windows.Data.CollectionViewSource.Filter>.</span><span class="sxs-lookup"><span data-stu-id="4569d-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="4569d-114">V následujícím příkladu je `listingDataView` instance <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="4569d-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="4569d-115">Následující příklad ukazuje implementaci obslužné rutiny události Filter `ShowOnlyBargainsFilter`.</span><span class="sxs-lookup"><span data-stu-id="4569d-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="4569d-116">Tato obslužná rutina události používá vlastnost <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> k vyfiltrování `AuctionItem` objektů, které mají `CurrentPrice` $25 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="4569d-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4569d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4569d-117">See also</span></span>

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [<span data-ttu-id="4569d-118">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4569d-118">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4569d-119">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="4569d-119">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="4569d-120">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="4569d-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
