---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 3a17d6cd5b723dcde4d8dc7059c9f416308f73db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082656"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="1a5b0-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="1a5b0-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="1a5b0-103">Tento příklad ukazuje, jak implementovat scénář hlavní podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a5b0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a5b0-104">Example</span></span>  
 <span data-ttu-id="1a5b0-105">V tomto příkladu `LeagueList` je kolekce `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="1a5b0-106">Každý `League` má `Name` a kolekce `Divisions`a každý `Division` má název a kolekci `Teams`.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="1a5b0-107">Každý `Team` má název týmu.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="1a5b0-108">Zde je snímek obrazovky v příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="1a5b0-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automaticky sleduje požadovaná nastavení `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazí se odpovídající data.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="1a5b0-110">`Teams` <xref:System.Windows.Controls.ListBox> Sleduje výběry do dalších dvou <xref:System.Windows.Controls.ListBox> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Snímek obrazovky zobrazující hlavní&#45;příklad scénáře podrobností.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="1a5b0-112">Jsou dvě věci v tomto příkladu si všimněte:</span><span class="sxs-lookup"><span data-stu-id="1a5b0-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="1a5b0-113">Tři <xref:System.Windows.Controls.ListBox> ke stejnému zdroji vytvoření vazby ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="1a5b0-114">Můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost vazby, kterou úroveň dat má být <xref:System.Windows.Controls.ListBox> k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="1a5b0-115">Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` na <xref:System.Windows.Controls.ListBox> ovládací prvky, které sledujete výběr.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="1a5b0-116">Nastavení této vlastnosti se zajistí, že je vybraná položka vždy nastavena jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="1a5b0-117">Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a Měna.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="1a5b0-118">Postup se mírně liší, když používáte [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span><span class="sxs-lookup"><span data-stu-id="1a5b0-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="1a5b0-119">Příklad najdete v tématu [použití vzoru seznam-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="1a5b0-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5b0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a5b0-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="1a5b0-121">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="1a5b0-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="1a5b0-122">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="1a5b0-122">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="1a5b0-123">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="1a5b0-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="1a5b0-124">– postupy</span><span class="sxs-lookup"><span data-stu-id="1a5b0-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
