---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 36eded28085aec3aaea1a2351ae3babc6ad6c700
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689637"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="530df-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="530df-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="530df-103">Tento příklad ukazuje, jak implementovat scénář hlavní podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="530df-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="530df-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="530df-104">Example</span></span>  
 <span data-ttu-id="530df-105">V tomto příkladu `LeagueList` je kolekce `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="530df-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="530df-106">Každý `League` má `Name` a kolekce `Divisions`a každý `Division` má název a kolekci `Teams`.</span><span class="sxs-lookup"><span data-stu-id="530df-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="530df-107">Každý `Team` má název týmu.</span><span class="sxs-lookup"><span data-stu-id="530df-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="530df-108">Zde je snímek obrazovky v příkladu.</span><span class="sxs-lookup"><span data-stu-id="530df-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="530df-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automaticky sleduje požadovaná nastavení `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazí se odpovídající data.</span><span class="sxs-lookup"><span data-stu-id="530df-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="530df-110">`Teams` <xref:System.Windows.Controls.ListBox> Sleduje výběry do dalších dvou <xref:System.Windows.Controls.ListBox> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="530df-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="530df-111">![Hlavní&#45;podrobný příklad](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="530df-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="530df-112">Jsou dvě věci v tomto příkladu si všimněte:</span><span class="sxs-lookup"><span data-stu-id="530df-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="530df-113">Tři <xref:System.Windows.Controls.ListBox> ke stejnému zdroji vytvoření vazby ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="530df-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="530df-114">Můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost vazby, kterou úroveň dat má být <xref:System.Windows.Controls.ListBox> k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="530df-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="530df-115">Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` na <xref:System.Windows.Controls.ListBox> ovládací prvky, které sledujete výběr.</span><span class="sxs-lookup"><span data-stu-id="530df-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="530df-116">Nastavení této vlastnosti se zajistí, že je vybraná položka vždy nastavena jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="530df-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="530df-117">Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a Měna.</span><span class="sxs-lookup"><span data-stu-id="530df-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="530df-118">Postup se mírně liší, když používáte [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span><span class="sxs-lookup"><span data-stu-id="530df-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="530df-119">Příklad najdete v tématu [použití vzoru seznam-podrobnosti s hierarchickými daty XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="530df-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="530df-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="530df-120">See also</span></span>
- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="530df-121">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="530df-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="530df-122">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="530df-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="530df-123">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="530df-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="530df-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="530df-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
