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
