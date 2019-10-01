---
title: 'Postupy: Připojení ke zdroji dat ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697141"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Postupy: Připojení ke zdroji dat ADO.NET

Tento příklad ukazuje, jak navazovat ovládací prvek [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> na ADO.NET `DataSet`.

## <a name="example"></a>Příklad

V tomto příkladu je objekt `OleDbConnection` použit pro připojení ke zdroji dat, který je soubor `Access MDB`, který je uveden v připojovacím řetězci. Po navázání spojení se vytvoří objekt `OleDbDataAdapter`. Objekt `OleDbDataAdapter` spustí příkaz SELECT jazyk SQL (Structured Query Language) (SQL) pro načtení sady záznamů z databáze. Výsledky z příkazu SQL jsou uloženy v `DataTable` `DataSet` voláním metody `Fill` `OleDbDataAdapter`. @No__t-0 v tomto příkladu je pojmenován `BookTable`. Příklad potom nastaví vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> na objekt `DataSet`.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Potom můžeme Navazovat vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> na `BookTable` `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` je <xref:System.Windows.DataTemplate> definující způsob zobrazení dat:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

@No__t-0 převede `int` na barvu. Při použití tohoto převaděče se barva <xref:System.Windows.Controls.TextBlock.Background%2A> třetího <xref:System.Windows.Controls.TextBlock> zobrazí zelenou, pokud je hodnota `NumPages` menší než 350 a červená, jinak. Zde se nezobrazuje implementace převaděče.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.BindingListCollectionView>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
