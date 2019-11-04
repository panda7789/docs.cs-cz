---
title: 'Postupy: Připojení k výsledkům dotazu LINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d21ac5f366e001ea76d6eda64ed62583248796f6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454412"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Postupy: Připojení k výsledkům dotazu LINQ

Tento příklad ukazuje, jak spustit dotaz LINQ a následně vytvořit vazby k výsledkům.

## <a name="example"></a>Příklad

Následující příklad vytvoří dvě seznam polí. První rozevírací seznam obsahuje tři položky seznamu.

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

Výběr položky z prvního seznamu vyvolá následující obslužnou rutinu události. V tomto příkladu je `Tasks` kolekce objektů `Task`. Třída `Task` obsahuje vlastnost s názvem `Priority`. Tato obslužná rutina události spustí dotaz LINQ, který vrátí kolekci `Task` objektů, které mají vybranou hodnotu priority, a poté nastaví jako <xref:System.Windows.FrameworkElement.DataContext%2A>:

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

Druhý rozevírací seznam se váže k této kolekci, protože jeho <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> hodnota je nastavena na `{Binding}`. V důsledku toho zobrazí vrácenou kolekci (na základě <xref:System.Windows.DataTemplate>`myTaskTemplate`).

## <a name="see-also"></a>Viz také:

- [Zpřístupnění dat pro vazbu v jazyku XAML](how-to-make-data-available-for-binding-in-xaml.md)
- [Vytvoření vazby ke kolekci a zobrazení informací podle výběru](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Novinky ve verzi 4.5 grafického subsystému WPF](../getting-started/whats-new.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
