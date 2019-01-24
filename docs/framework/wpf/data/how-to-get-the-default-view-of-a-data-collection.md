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
ms.openlocfilehash: 386c25998c85de2f674200fe7d269ae2fdabd72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588398"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="77088-102">Postupy: Načtení výchozího zobrazení datové kolekce</span><span class="sxs-lookup"><span data-stu-id="77088-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="77088-103">Zobrazení umožňují kolekci dat prohlížení různými způsoby v závislosti na řazení, filtrování nebo kritéria pro seskupení.</span><span class="sxs-lookup"><span data-stu-id="77088-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="77088-104">Každá kolekce má jedno sdílené výchozí zobrazení, který se používá jako zdroj skutečná vazba při vazbu určuje jako svůj zdroj kolekce.</span><span class="sxs-lookup"><span data-stu-id="77088-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="77088-105">Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="77088-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77088-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="77088-106">Example</span></span>  
 <span data-ttu-id="77088-107">Vytvořte zobrazení, potřebujete odkaz na objekt do kolekce.</span><span class="sxs-lookup"><span data-stu-id="77088-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="77088-108">Odkazování na vlastní objekt použití modelu code-behind získáním kontext dat, získání vlastnosti zdroje dat, nebo získání vlastnosti vazby je možné získat tímto datovým objektem.</span><span class="sxs-lookup"><span data-stu-id="77088-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="77088-109">Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datový objekt a použít ho přímo získat výchozí kolekci zobrazení pro tuto kolekci.</span><span class="sxs-lookup"><span data-stu-id="77088-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="77088-110">V tomto příkladu je kořenovým elementem <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="77088-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="77088-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Je nastavena na *myDataSource*, která odkazuje na poskytovatele dat, která je <xref:System.Collections.ObjectModel.ObservableCollection%601> z *pořadí* objekty.</span><span class="sxs-lookup"><span data-stu-id="77088-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="77088-112">Alternativně můžete vytvořit instanci a vytvořit vazbu na vlastní kolekce zobrazení pomocí <xref:System.Windows.Data.CollectionViewSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="77088-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="77088-113">Toto zobrazení kolekce ovládacích prvků, které se přímo spojit pouze sdílí.</span><span class="sxs-lookup"><span data-stu-id="77088-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="77088-114">Příklad, zjistit, jak vytvořit zobrazení tématu [přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="77088-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="77088-115">Příklady funkce poskytované službou zobrazení kolekcí najdete v tématu [řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), a [přejít přes objektů v datech CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="77088-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77088-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77088-116">See also</span></span>
- [<span data-ttu-id="77088-117">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="77088-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="77088-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="77088-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
