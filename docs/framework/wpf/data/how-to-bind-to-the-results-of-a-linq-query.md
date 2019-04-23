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
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Postupy: Vytvoření vazby k výsledkům dotazu LINQ
Tento příklad ukazuje, jak spustit dotaz LINQ a potom připojení k výsledkům.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě pole se seznamem. První seznam obsahuje tři položky seznamu.  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Výběrem položky z prvního seznamu vyvolá následující obslužnou rutinu události. V tomto příkladu `Tasks` je kolekce `Task` objekty. `Task` Třída nemá vlastnost s názvem `Priority`. Tato obslužná rutina události spustí dotaz LINQ, který vrátí kolekci `Task` objekty, které mají hodnotu priority vybrané a pak nastaví jako <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 Druhý seznam vytvoří vazbu na tuto kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nastavena na hodnotu `{Binding}`. V důsledku toho se zobrazí vrácená kolekce (na základě `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Viz také:

- [Zpřístupnění dat pro vazbu v jazyku XAML](how-to-make-data-available-for-binding-in-xaml.md)
- [Vytvoření vazby ke kolekci a zobrazení informací podle výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Novinky ve verzi 4.5 grafického subsystému WPF](../getting-started/whats-new.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
