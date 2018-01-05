---
title: "Postupy: Připojení k výsledkům dotazu LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad4969d80f7bd801ec738fa40e8b2d4ab9deefad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="a4406-102">Postupy: Připojení k výsledkům dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="a4406-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="a4406-103">Tento příklad ukazuje, jak spustit dotaz LINQ a pak vytvořte vazbu s výsledky.</span><span class="sxs-lookup"><span data-stu-id="a4406-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4406-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4406-104">Example</span></span>  
 <span data-ttu-id="a4406-105">Následující příklad vytvoří dva seznamy.</span><span class="sxs-lookup"><span data-stu-id="a4406-105">The following example creates two list boxes.</span></span> <span data-ttu-id="a4406-106">První pole se seznamem obsahuje tři položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="a4406-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="a4406-107">Výběrem položky z první pole se seznamem vyvolá následující obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a4406-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="a4406-108">V tomto příkladu `Tasks` je kolekce `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="a4406-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="a4406-109">`Task` Třída má vlastnost s názvem `Priority`.</span><span class="sxs-lookup"><span data-stu-id="a4406-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="a4406-110">Tuto obslužnou rutinu události spustí dotaz LINQ, který vrátí kolekce `Task` objekty, které mají hodnotu priority vybrané a nastaví, jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="a4406-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="a4406-111">Druhé pole se seznamem váže na tuto kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nastavena na hodnotu `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="a4406-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="a4406-112">Výsledkem je, zobrazí se vrácená kolekce (na základě `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="a4406-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4406-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4406-113">See Also</span></span>  
 [<span data-ttu-id="a4406-114">Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="a4406-114">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [<span data-ttu-id="a4406-115">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="a4406-115">Bind to a Collection and Display Information Based on Selection</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [<span data-ttu-id="a4406-116">Novinky ve verzi 4.5 grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="a4406-116">What's New in WPF Version 4.5</span></span>](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [<span data-ttu-id="a4406-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="a4406-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="a4406-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a4406-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
