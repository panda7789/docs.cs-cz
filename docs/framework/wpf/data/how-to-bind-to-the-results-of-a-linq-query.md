---
title: 'Postupy: Vytvoření vazby k výsledkům dotazu LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 5464ee9c59a7c99a83774a7535b9b3c422c1d2e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185897"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="48f2a-102">Postupy: Vytvoření vazby k výsledkům dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="48f2a-102">How to: Bind to the Results of a LINQ Query</span></span>
<span data-ttu-id="48f2a-103">Tento příklad ukazuje, jak spustit dotaz LINQ a potom připojení k výsledkům.</span><span class="sxs-lookup"><span data-stu-id="48f2a-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48f2a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="48f2a-104">Example</span></span>  
 <span data-ttu-id="48f2a-105">Následující příklad vytvoří dvě pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="48f2a-105">The following example creates two list boxes.</span></span> <span data-ttu-id="48f2a-106">První seznam obsahuje tři položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="48f2a-106">The first list box contains three list items.</span></span>  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="48f2a-107">Výběrem položky z prvního seznamu vyvolá následující obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="48f2a-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="48f2a-108">V tomto příkladu `Tasks` je kolekce `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="48f2a-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="48f2a-109">`Task` Třída nemá vlastnost s názvem `Priority`.</span><span class="sxs-lookup"><span data-stu-id="48f2a-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="48f2a-110">Tato obslužná rutina události spustí dotaz LINQ, který vrátí kolekci `Task` objekty, které mají hodnotu priority vybrané a pak nastaví jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="48f2a-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 <span data-ttu-id="48f2a-111">Druhý seznam vytvoří vazbu na tuto kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nastavena na hodnotu `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="48f2a-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="48f2a-112">V důsledku toho se zobrazí vrácená kolekce (na základě `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="48f2a-112">As a result, it displays the returned collection (based on the `myTaskTemplate`<xref:System.Windows.DataTemplate>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f2a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48f2a-113">See also</span></span>

- [<span data-ttu-id="48f2a-114">Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="48f2a-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="48f2a-115">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="48f2a-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="48f2a-116">Novinky ve verzi 4.5 grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="48f2a-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="48f2a-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="48f2a-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="48f2a-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="48f2a-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
