---
title: 'Postupy: Vytvoření vazby ke kolekci a zobrazení informací podle výběru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: bb7d4c89e63982a3052857dcb50d04d36d9517dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314386"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="3ca0a-102">Postupy: Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="3ca0a-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="3ca0a-103">V jednoduchém scénáři hlavní podrobnosti máte vázaný na data <xref:System.Windows.Controls.ItemsControl> například <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="3ca0a-104">Na základě výběru uživatelem, zobrazíte další informace o vybrané položce.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="3ca0a-105">Tento příklad ukazuje, jak tento scénář implementovat.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ca0a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ca0a-106">Example</span></span>  
 <span data-ttu-id="3ca0a-107">V tomto příkladu `People` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="3ca0a-108">To `Person` třída obsahuje tři vlastnosti: `FirstName`, `LastName`, a `HomeTown`, typu `string`.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="3ca0a-109"><xref:System.Windows.Controls.ContentControl> Používá následující <xref:System.Windows.DataTemplate> , který definuje jak informace `Person` se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="3ca0a-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="3ca0a-110">Zde je snímek obrazovky vzorové postupy.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="3ca0a-111"><xref:System.Windows.Controls.ContentControl> Jsou uvedeny vlastnosti osoby vybrali.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="3ca0a-112">![Vytvoření vazby ke kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="3ca0a-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="3ca0a-113">Jsou dvě věci v tomto příkladu si všimněte:</span><span class="sxs-lookup"><span data-stu-id="3ca0a-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="3ca0a-114"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> vytvoření vazby ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="3ca0a-115"><xref:System.Windows.Data.Binding.Path%2A> Vlastnosti obou vazby nejsou zadané, protože oba ovládací prvky jsou vazby objektu celou kolekci.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="3ca0a-116">Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` aby to fungovalo.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="3ca0a-117">Nastavení této vlastnosti se zajistí, že je vybraná položka vždy nastavena jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="3ca0a-118">Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a Měna.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="3ca0a-119">Všimněte si, že `Person` třídy přepsání `ToString` metodu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="3ca0a-120">Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volání `ToString` a zobrazí řetězec představující jednotlivých objektů v vázané kolekce.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="3ca0a-121">To je důvod, proč každý `Person` se zobrazí jako první název v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="3ca0a-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="3ca0a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ca0a-122">See also</span></span>

- [<span data-ttu-id="3ca0a-123">Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="3ca0a-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="3ca0a-124">Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="3ca0a-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="3ca0a-125">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="3ca0a-125">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3ca0a-126">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="3ca0a-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="3ca0a-127">– postupy</span><span class="sxs-lookup"><span data-stu-id="3ca0a-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
