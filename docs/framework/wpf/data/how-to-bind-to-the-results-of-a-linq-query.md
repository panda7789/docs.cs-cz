---
title: 'Postupy: Připojení k výsledkům dotazu LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d374bb69b6b7e022497403b9591b27e9ad7e2395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Postupy: Připojení k výsledkům dotazu LINQ
Tento příklad ukazuje, jak spustit dotaz LINQ a pak vytvořte vazbu s výsledky.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva seznamy. První pole se seznamem obsahuje tři položky seznamu.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Výběrem položky z první pole se seznamem vyvolá následující obslužné rutiny události. V tomto příkladu `Tasks` je kolekce `Task` objekty. `Task` Třída má vlastnost s názvem `Priority`. Tuto obslužnou rutinu události spustí dotaz LINQ, který vrátí kolekce `Task` objekty, které mají hodnotu priority vybrané a nastaví, jako <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 Druhé pole se seznamem váže na tuto kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nastavena na hodnotu `{Binding}`. Výsledkem je, zobrazí se vrácená kolekce (na základě `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Viz také  
 [Zpřístupnění dat pro vazbu v jazyku XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [Vytvoření vazby ke kolekci a zobrazení informací podle výběru](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Novinky ve verzi 4.5 grafického subsystému WPF](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
