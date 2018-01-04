---
title: "Postupy: Připojení ke kolekci a zobrazení informací podle výběru"
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
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751025470b566ef1e735e4ddd192cfd8fc354ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="bf982-102">Postupy: Připojení ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="bf982-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="bf982-103">V jednoduchém scénáři seznam podrobnosti máte vázané na data <xref:System.Windows.Controls.ItemsControl> například <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="bf982-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="bf982-104">Na základě výběru, můžete zobrazit další informace o vybrané položce.</span><span class="sxs-lookup"><span data-stu-id="bf982-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="bf982-105">Tento příklad ukazuje, jak implementovat tento scénář.</span><span class="sxs-lookup"><span data-stu-id="bf982-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf982-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf982-106">Example</span></span>  
 <span data-ttu-id="bf982-107">V tomto příkladu `People` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="bf982-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="bf982-108">To `Person` třída obsahuje tři vlastnosti: `FirstName`, `LastName`, a `HomeTown`, všechny typu `string`.</span><span class="sxs-lookup"><span data-stu-id="bf982-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="bf982-109"><xref:System.Windows.Controls.ContentControl> Používá následující <xref:System.Windows.DataTemplate> , který definuje jak informace `Person` se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="bf982-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="bf982-110">Zde je snímek obrazovky co vytváří v příkladu.</span><span class="sxs-lookup"><span data-stu-id="bf982-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="bf982-111"><xref:System.Windows.Controls.ContentControl> Zobrazí vlastnosti vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="bf982-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="bf982-112">![Vazby ke kolekci](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="bf982-112">![Binding to a collection](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="bf982-113">Dvě věci Všimněte v tomto příkladu jsou:</span><span class="sxs-lookup"><span data-stu-id="bf982-113">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="bf982-114"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> vytvořit vazbu ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="bf982-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="bf982-115"><xref:System.Windows.Data.Binding.Path%2A> Vlastnosti obou vazby nejsou zadané, protože oba ovládací prvky jsou vazby k objektu celou kolekci.</span><span class="sxs-lookup"><span data-stu-id="bf982-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2.  <span data-ttu-id="bf982-116">Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` pro tento postup.</span><span class="sxs-lookup"><span data-stu-id="bf982-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="bf982-117">Nastavení této vlastnosti zajistí, že vybraná položka je vždycky nastavený jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf982-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="bf982-118">Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měny.</span><span class="sxs-lookup"><span data-stu-id="bf982-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="bf982-119">Všimněte si, že `Person` třídy přepsání `ToString` metoda následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bf982-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="bf982-120">Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volání `ToString` a zobrazí řetězcovou reprezentaci jednotlivých objektů v vázané kolekce.</span><span class="sxs-lookup"><span data-stu-id="bf982-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="bf982-121">To je důvod, proč každý `Person` se zobrazí jako první název v <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="bf982-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="bf982-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf982-122">See Also</span></span>  
 [<span data-ttu-id="bf982-123">Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="bf982-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [<span data-ttu-id="bf982-124">Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="bf982-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [<span data-ttu-id="bf982-125">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="bf982-125">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="bf982-126">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="bf982-126">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="bf982-127">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="bf982-127">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
