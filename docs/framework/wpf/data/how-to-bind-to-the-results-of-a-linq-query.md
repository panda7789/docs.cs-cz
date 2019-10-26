---
title: 'Postupy: Připojení k výsledkům dotazu LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920126"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="4ce7f-102">Postupy: Připojení k výsledkům dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="4ce7f-102">How to: Bind to the Results of a LINQ Query</span></span>

<span data-ttu-id="4ce7f-103">Tento příklad ukazuje, jak spustit dotaz LINQ a následně vytvořit vazby k výsledkům.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>

## <a name="example"></a><span data-ttu-id="4ce7f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ce7f-104">Example</span></span>

<span data-ttu-id="4ce7f-105">Následující příklad vytvoří dvě seznam polí.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-105">The following example creates two list boxes.</span></span> <span data-ttu-id="4ce7f-106">První rozevírací seznam obsahuje tři položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-106">The first list box contains three list items.</span></span>

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

<span data-ttu-id="4ce7f-107">Výběr položky z prvního seznamu vyvolá následující obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="4ce7f-108">V tomto příkladu je `Tasks` kolekce objektů `Task`.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="4ce7f-109">Třída `Task` obsahuje vlastnost s názvem `Priority`.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="4ce7f-110">Tato obslužná rutina události spustí dotaz LINQ, který vrátí kolekci `Task` objektů, které mají vybranou hodnotu priority, a poté nastaví jako <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="4ce7f-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

<span data-ttu-id="4ce7f-111">Druhý rozevírací seznam se váže k této kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> hodnota je nastavena na `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="4ce7f-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="4ce7f-112">V důsledku toho zobrazí vrácenou kolekci (na základě <xref:System.Windows.DataTemplate>`myTaskTemplate`).</span><span class="sxs-lookup"><span data-stu-id="4ce7f-112">As a result, it displays the returned collection (based on the `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ce7f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ce7f-113">See also</span></span>

- [<span data-ttu-id="4ce7f-114">Zpřístupnění dat pro vazbu v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="4ce7f-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="4ce7f-115">Vytvoření vazby ke kolekci a zobrazení informací podle výběru</span><span class="sxs-lookup"><span data-stu-id="4ce7f-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="4ce7f-116">Novinky ve verzi 4.5 grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="4ce7f-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="4ce7f-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4ce7f-117">Data Binding Overview</span></span>](data-binding-overview.md)
