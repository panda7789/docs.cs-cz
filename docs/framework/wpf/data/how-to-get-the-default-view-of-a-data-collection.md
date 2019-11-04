---
title: 'Postupy: Načtení výchozího zobrazení datové kolekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459127"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="c2cf3-102">Postupy: Načtení výchozího zobrazení datové kolekce</span><span class="sxs-lookup"><span data-stu-id="c2cf3-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="c2cf3-103">Zobrazení umožňují, aby se stejná kolekce dat zobrazila různými způsoby v závislosti na řazení, filtrování nebo kritériích seskupení.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="c2cf3-104">Každá kolekce má jedno sdílené výchozí zobrazení, které se používá jako skutečný zdroj vazby, když vazba jako zdroj určí kolekci.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="c2cf3-105">Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2cf3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2cf3-106">Example</span></span>  
 <span data-ttu-id="c2cf3-107">Chcete-li vytvořit zobrazení, budete potřebovat odkaz na objekt v kolekci.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="c2cf3-108">Tento datový objekt lze získat odkazem na vlastní objekt kódu na pozadí získáním kontextu dat, získáním vlastnosti zdroje dat nebo získáním vlastnosti vazby.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="c2cf3-109">Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datového objektu a použít ho k přímému získání výchozího zobrazení kolekce pro tuto kolekci.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="c2cf3-110">V tomto příkladu je kořenovým prvkem <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="c2cf3-111"><xref:System.Windows.FrameworkElement.DataContext%2A> je nastavená na *myDataSource*, která odkazuje na poskytovatele dat, který je <xref:System.Collections.ObjectModel.ObservableCollection%601> objektů *Order* .</span><span class="sxs-lookup"><span data-stu-id="c2cf3-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="c2cf3-112">Alternativně můžete vytvořit instanci a vytvořit propojení s vlastním zobrazením kolekce pomocí třídy <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="c2cf3-113">Toto zobrazení kolekce je sdíleno pouze ovládacími prvky, které přímo na něj vážou.</span><span class="sxs-lookup"><span data-stu-id="c2cf3-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="c2cf3-114">Příklad naleznete v části Vytvoření zobrazení v tématu [Přehled vytváření datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2cf3-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c2cf3-115">Příklady funkcí poskytovaných zobrazením kolekce najdete v tématech [řazení dat v zobrazení](how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](how-to-filter-data-in-a-view.md)a [procházení objektů v CollectionView dat](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="c2cf3-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cf3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2cf3-116">See also</span></span>

- [<span data-ttu-id="c2cf3-117">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="c2cf3-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="c2cf3-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c2cf3-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
