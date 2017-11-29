---
title: "Postupy: Načtení výchozího zobrazení datové kolekce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d1ababcb7a00496b59005b5e90f875511fefc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="9675c-102">Postupy: Načtení výchozího zobrazení datové kolekce</span><span class="sxs-lookup"><span data-stu-id="9675c-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="9675c-103">Zobrazení povolit stejné shromažďování dat lze zobrazit v různými způsoby v závislosti na třídění, filtrování nebo kritéria seskupení.</span><span class="sxs-lookup"><span data-stu-id="9675c-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="9675c-104">Všechny kolekce má jeden sdílený výchozí zobrazení, které slouží jako zdroj skutečná vazba, pokud vazba určuje jako svůj zdroj kolekce.</span><span class="sxs-lookup"><span data-stu-id="9675c-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="9675c-105">Tento příklad ukazuje, jak získat výchozí zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="9675c-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9675c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9675c-106">Example</span></span>  
 <span data-ttu-id="9675c-107">Chcete-li vytvořit zobrazení, je třeba odkaz na objekt do kolekce.</span><span class="sxs-lookup"><span data-stu-id="9675c-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="9675c-108">Tento objekt data je možné získat vlastní objekt kódu odkazuje získáním kontextu dat tím, že získáme vlastnosti zdroje dat nebo tím, že získáme vlastnost vazby.</span><span class="sxs-lookup"><span data-stu-id="9675c-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="9675c-109">Tento příklad ukazuje, jak získat <xref:System.Windows.FrameworkElement.DataContext%2A> datový objekt a použijte ji přímo získat výchozí kolekci zobrazení pro tuto kolekci.</span><span class="sxs-lookup"><span data-stu-id="9675c-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="9675c-110">V tomto příkladu je kořenový element <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9675c-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9675c-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Je nastaven na *myDataSource*, které odkazuje na zprostředkovatele dat, který je <xref:System.Collections.ObjectModel.ObservableCollection%601> z *pořadí* objekty.</span><span class="sxs-lookup"><span data-stu-id="9675c-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="9675c-112">Alternativně můžete vytvořit instanci a vytvoření vazby na vlastní kolekce zobrazení pomocí <xref:System.Windows.Data.CollectionViewSource> třídy.</span><span class="sxs-lookup"><span data-stu-id="9675c-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="9675c-113">Toto zobrazení kolekce pouze sdílí ovládacích prvků, které přímo svázat.</span><span class="sxs-lookup"><span data-stu-id="9675c-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="9675c-114">Příklad, naleznete v části Postup vytvoření zobrazení tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9675c-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="9675c-115">Příklady funkce poskytované službou zobrazení kolekce najdete v tématu [řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), a [přejděte prostřednictvím objekty v dat CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="9675c-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9675c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9675c-116">See Also</span></span>  
 [<span data-ttu-id="9675c-117">Řazení a seskupování dat pomocí zobrazení v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="9675c-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="9675c-118">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="9675c-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
