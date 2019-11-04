---
title: 'Postupy: Připojení ke kolekci a zobrazení informací podle výběru'
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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459154"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="43053-102">Postupy: Připojení ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="43053-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="43053-103">V jednoduchém scénáři hlavní-podrobnosti máte <xref:System.Windows.Controls.ItemsControl> vázaný na data, jako je například <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="43053-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="43053-104">Na základě výběru uživatele zobrazíte další informace o vybrané položce.</span><span class="sxs-lookup"><span data-stu-id="43053-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="43053-105">Tento příklad ukazuje, jak implementovat tento scénář.</span><span class="sxs-lookup"><span data-stu-id="43053-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43053-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="43053-106">Example</span></span>  
 <span data-ttu-id="43053-107">V tomto příkladu je `People` <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy `Person`.</span><span class="sxs-lookup"><span data-stu-id="43053-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="43053-108">Tato třída `Person` obsahuje tři vlastnosti: `FirstName`, `LastName`a `HomeTown`, všechny typy `string`.</span><span class="sxs-lookup"><span data-stu-id="43053-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="43053-109"><xref:System.Windows.Controls.ContentControl> používá následující <xref:System.Windows.DataTemplate> definující způsob, jakým jsou uvedeny informace o `Person`:</span><span class="sxs-lookup"><span data-stu-id="43053-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="43053-110">Následuje snímek obrazovky s tím, co příklad vytváří.</span><span class="sxs-lookup"><span data-stu-id="43053-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="43053-111"><xref:System.Windows.Controls.ContentControl> zobrazuje další vlastnosti vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="43053-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="43053-112">![Vazba na kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="43053-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="43053-113">V tomto příkladu si všimněte těchto dvou věcí:</span><span class="sxs-lookup"><span data-stu-id="43053-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="43053-114"><xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ContentControl> se váže ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="43053-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="43053-115">Vlastnosti <xref:System.Windows.Data.Binding.Path%2A> obou vazeb nejsou zadány, protože oba ovládací prvky jsou vázány na celý objekt kolekce.</span><span class="sxs-lookup"><span data-stu-id="43053-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="43053-116">Aby tato vlastnost fungovala, je nutné nastavit vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="43053-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="43053-117">Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="43053-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="43053-118">Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měnu.</span><span class="sxs-lookup"><span data-stu-id="43053-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="43053-119">Všimněte si, že třída `Person` přepisuje metodu `ToString` následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="43053-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="43053-120">Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volá `ToString` a zobrazí řetězcovou reprezentaci každého objektu v vázané kolekci.</span><span class="sxs-lookup"><span data-stu-id="43053-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="43053-121">To je důvod, proč se každý `Person` v <xref:System.Windows.Controls.ListBox>zobrazí jako křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="43053-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="43053-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43053-122">See also</span></span>

- [<span data-ttu-id="43053-123">Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="43053-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="43053-124">Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="43053-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="43053-125">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="43053-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="43053-126">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="43053-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="43053-127">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="43053-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
