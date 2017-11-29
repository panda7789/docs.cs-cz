---
title: "Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a><span data-ttu-id="8d621-102">Postupy: Použití vzoru seznam-podrobnosti s hierarchickými daty</span><span class="sxs-lookup"><span data-stu-id="8d621-102">How to: Use the Master-Detail Pattern with Hierarchical Data</span></span>
<span data-ttu-id="8d621-103">Tento příklad ukazuje, jak implementovat scénář seznam podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="8d621-103">This example shows how to implement the master-detail scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d621-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d621-104">Example</span></span>  
 <span data-ttu-id="8d621-105">V tomto příkladu `LeagueList` je kolekce `Leagues`.</span><span class="sxs-lookup"><span data-stu-id="8d621-105">In this example, `LeagueList` is a collection of `Leagues`.</span></span> <span data-ttu-id="8d621-106">Každý `League` má `Name` a kolekce `Divisions`a každou `Division` má název a kolekci `Teams`.</span><span class="sxs-lookup"><span data-stu-id="8d621-106">Each `League` has a `Name` and a collection of `Divisions`, and each `Division` has a name and a collection of `Teams`.</span></span> <span data-ttu-id="8d621-107">Každý `Team` má název týmu.</span><span class="sxs-lookup"><span data-stu-id="8d621-107">Each `Team` has a team name.</span></span>  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 <span data-ttu-id="8d621-108">Zde je snímek obrazovky v příkladu.</span><span class="sxs-lookup"><span data-stu-id="8d621-108">The following is a screenshot of the example.</span></span> <span data-ttu-id="8d621-109">`Divisions` <xref:System.Windows.Controls.ListBox> Automaticky sleduje výběrů v `Leagues` <xref:System.Windows.Controls.ListBox> a zobrazit odpovídající data.</span><span class="sxs-lookup"><span data-stu-id="8d621-109">The `Divisions` <xref:System.Windows.Controls.ListBox> automatically tracks selections in the `Leagues` <xref:System.Windows.Controls.ListBox> and display the corresponding data.</span></span> <span data-ttu-id="8d621-110">`Teams` <xref:System.Windows.Controls.ListBox> Sleduje výběrů v další dvě <xref:System.Windows.Controls.ListBox> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="8d621-110">The `Teams` <xref:System.Windows.Controls.ListBox> tracks selections in the other two <xref:System.Windows.Controls.ListBox> controls.</span></span>  
  
 <span data-ttu-id="8d621-111">![Hlavní & č. 45; podrobnosti o příklad](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span><span class="sxs-lookup"><span data-stu-id="8d621-111">![Master&#45;detail example](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")</span></span>  
  
 <span data-ttu-id="8d621-112">Dvě věci Všimněte v tomto příkladu jsou:</span><span class="sxs-lookup"><span data-stu-id="8d621-112">The two things to notice in this example are:</span></span>  
  
1.  <span data-ttu-id="8d621-113">Tří <xref:System.Windows.Controls.ListBox> ovládací prvky vazby ke stejnému zdroji.</span><span class="sxs-lookup"><span data-stu-id="8d621-113">The three <xref:System.Windows.Controls.ListBox> controls bind to the same source.</span></span> <span data-ttu-id="8d621-114">Můžete nastavit <xref:System.Windows.Data.Binding.Path%2A> vlastnost vazby k určení, kterou úroveň dat chcete <xref:System.Windows.Controls.ListBox> k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="8d621-114">You set the <xref:System.Windows.Data.Binding.Path%2A> property of the binding to specify which level of data you want the <xref:System.Windows.Controls.ListBox> to display.</span></span>  
  
2.  <span data-ttu-id="8d621-115">Je nutné nastavit <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost `true` na <xref:System.Windows.Controls.ListBox> ovládací prvky, které na výběr jsou sledování.</span><span class="sxs-lookup"><span data-stu-id="8d621-115">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` on the <xref:System.Windows.Controls.ListBox> controls of which the selection you are tracking.</span></span> <span data-ttu-id="8d621-116">Nastavení této vlastnosti zajistí, že vybraná položka je vždycky nastavený jako <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d621-116">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="8d621-117">Případně pokud <xref:System.Windows.Controls.ListBox> ho načte data z <xref:System.Windows.Data.CollectionViewSource>, automaticky synchronizuje výběr a měny.</span><span class="sxs-lookup"><span data-stu-id="8d621-117">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="8d621-118">Při použití se mírně liší technika [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span><span class="sxs-lookup"><span data-stu-id="8d621-118">The technique is slightly different when you are using [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data.</span></span> <span data-ttu-id="8d621-119">Příklad, naleznete v části [použití vzoru seznam-podrobnosti s hierarchické Data XML](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="8d621-119">For an example, see [Use the Master-Detail Pattern with Hierarchical XML Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d621-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d621-120">See Also</span></span>  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [<span data-ttu-id="8d621-121">Vytvořit vazbu na kolekce a zobrazované informace na základě výběru</span><span class="sxs-lookup"><span data-stu-id="8d621-121">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="8d621-122">Přehled vazba dat</span><span class="sxs-lookup"><span data-stu-id="8d621-122">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="8d621-123">Ukázka dat – přehled</span><span class="sxs-lookup"><span data-stu-id="8d621-123">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="8d621-124">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="8d621-124">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
