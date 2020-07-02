---
title: 'Postupy: Připojení ke kolekci a zobrazení informací podle výběru'
description: Podle tohoto příkladu se dozvíte, jak vytvořit vazby na kolekci a zobrazit informace na základě výběru v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619608"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="97cda-103">Postupy: Připojení ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="97cda-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="97cda-104">V jednoduchém scénáři hlavní-podrobnosti máte datovou vazbu, jako <xref:System.Windows.Controls.ItemsControl> je například <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="97cda-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="97cda-105">Na základě výběru uživatele zobrazíte další informace o vybrané položce.</span><span class="sxs-lookup"><span data-stu-id="97cda-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="97cda-106">Tento příklad ukazuje, jak implementovat tento scénář.</span><span class="sxs-lookup"><span data-stu-id="97cda-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97cda-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="97cda-107">Example</span></span>  
 <span data-ttu-id="97cda-108">V tomto příkladu `People` je typu <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` třídy.</span><span class="sxs-lookup"><span data-stu-id="97cda-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="97cda-109">Tato `Person` Třída obsahuje tři vlastnosti: `FirstName` , a `LastName` `HomeTown` , vše typu `string` .</span><span class="sxs-lookup"><span data-stu-id="97cda-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="97cda-110"><xref:System.Windows.Controls.ContentControl>Používá následující <xref:System.Windows.DataTemplate> , které definuje způsob předložení informací o typu `Person` :</span><span class="sxs-lookup"><span data-stu-id="97cda-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="97cda-111">Následuje snímek obrazovky s tím, co příklad vytváří.</span><span class="sxs-lookup"><span data-stu-id="97cda-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="97cda-112"><xref:System.Windows.Controls.ContentControl>Zobrazuje ostatní vlastnosti vybrané osoby.</span><span class="sxs-lookup"><span data-stu-id="97cda-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="97cda-113">![Vazba na kolekci](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="97cda-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="97cda-114">V tomto příkladu si všimněte těchto dvou věcí:</span><span class="sxs-lookup"><span data-stu-id="97cda-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="97cda-115"><xref:System.Windows.Controls.ListBox>A <xref:System.Windows.Controls.ContentControl> vytvoří vazby ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="97cda-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="97cda-116"><xref:System.Windows.Data.Binding.Path%2A>Vlastnosti obou vazeb nejsou zadány, protože oba ovládací prvky jsou svázány s celým objektem kolekce.</span><span class="sxs-lookup"><span data-stu-id="97cda-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="97cda-117">Aby <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> Tato vlastnost fungovala, je nutné ji nastavit na `true` .</span><span class="sxs-lookup"><span data-stu-id="97cda-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="97cda-118">Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="97cda-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="97cda-119">Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z a <xref:System.Windows.Data.CollectionViewSource> , synchronizuje výběr a měnu automaticky.</span><span class="sxs-lookup"><span data-stu-id="97cda-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="97cda-120">Všimněte si, že `Person` Třída Přepisuje `ToString` metodu následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="97cda-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="97cda-121">Ve výchozím nastavení <xref:System.Windows.Controls.ListBox> volá `ToString` a zobrazuje řetězcovou reprezentaci každého objektu v vázané kolekci.</span><span class="sxs-lookup"><span data-stu-id="97cda-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="97cda-122">To znamená, že každý `Person` se v nástroji zobrazí jako křestní jméno <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="97cda-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="97cda-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97cda-123">See also</span></span>

- [<span data-ttu-id="97cda-124">Použití vzoru hlavní-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="97cda-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="97cda-125">Použití vzoru seznam-podrobnosti s hierarchickými daty XML</span><span class="sxs-lookup"><span data-stu-id="97cda-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="97cda-126">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="97cda-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="97cda-127">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="97cda-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="97cda-128">– postupy</span><span class="sxs-lookup"><span data-stu-id="97cda-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
