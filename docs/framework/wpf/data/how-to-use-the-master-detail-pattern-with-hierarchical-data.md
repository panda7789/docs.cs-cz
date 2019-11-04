---
title: 'Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: 2e7d9ceed3ab8385f07d87ecdb92c0a99d410b40
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459078"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="9ba38-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="9ba38-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="9ba38-103">Tento příklad ukazuje, jak implementovat scénář hlavní-podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="9ba38-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ba38-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ba38-104">Example</span></span>  
 <span data-ttu-id="9ba38-105">V tomto příkladu je `LeagueList` kolekce `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="9ba38-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="9ba38-106">Každý `League` má `Name` a kolekci `Divisions`a každý `Division` má název a kolekci `Teams`.</span><span class="sxs-lookup"><span data-stu-id="9ba38-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="9ba38-107">Každý `Team` má název týmu.</span><span class="sxs-lookup"><span data-stu-id="9ba38-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="9ba38-108">Níže je příklad snímku.</span><span class="sxs-lookup"><span data-stu-id="9ba38-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="9ba38-109"><xref:System.Windows.Controls.ListBox> `Divisions` automaticky sleduje výběry v `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazují odpovídající data.</span><span class="sxs-lookup"><span data-stu-id="9ba38-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="9ba38-110">`Teams` <xref:System.Windows.Controls.ListBox> sleduje výběry v dalších dvou ovládacích prvcích <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="9ba38-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 ![Snímek obrazovky, který zobrazuje&#45;příklad scénáře hlavní podrobnosti.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 <span data-ttu-id="9ba38-112">V tomto příkladu si všimněte těchto dvou věcí:</span><span class="sxs-lookup"><span data-stu-id="9ba38-112">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="9ba38-113">Tři <xref:System.Windows.Controls.ListBox> ovládací prvky vážou ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="9ba38-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="9ba38-114">Vlastnost <xref:System.Windows.Data.Binding.Path%2A> vazby nastavíte tak, aby určovala, kterou úroveň dat má <xref:System.Windows.Controls.ListBox> zobrazit.</span><span class="sxs-lookup"><span data-stu-id="9ba38-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2. <span data-ttu-id="9ba38-115">Vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> musíte nastavit na `true` na ovládací prvky <xref:System.Windows.Controls.ListBox>, na kterých sledujete výběr.</span><span class="sxs-lookup"><span data-stu-id="9ba38-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="9ba38-116">Nastavení této vlastnosti zajistí, že se vybraná položka vždycky nastaví jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ba38-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="9ba38-117">Případně, pokud <xref:System.Windows.Controls.ListBox> získá data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měnu.</span><span class="sxs-lookup"><span data-stu-id="9ba38-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="9ba38-118">Technika je mírně odlišná, pokud používáte [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span><span class="sxs-lookup"><span data-stu-id="9ba38-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="9ba38-119">Příklad naleznete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty XML](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="9ba38-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba38-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ba38-120">See also</span></span>

- <xref:System.Windows.HierarchicalDataTemplate>
- [<span data-ttu-id="9ba38-121">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="9ba38-121">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="9ba38-122">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="9ba38-122">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9ba38-123">Přehled datových šablon</span><span class="sxs-lookup"><span data-stu-id="9ba38-123">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="9ba38-124">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9ba38-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
