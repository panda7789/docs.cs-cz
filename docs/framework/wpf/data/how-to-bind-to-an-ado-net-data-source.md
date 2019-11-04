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
ms.openlocfilehash: 0b3d7147f45bee5e8abd95bdc51c5f5f695cf830
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458403"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Postupy: Připojení ke zdroji dat ADO.NET

Tento příklad ukazuje, jak vytvořit vazby [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> ovládacího prvku na `DataSet`ADO.NET.

## <a name="example"></a>Příklad

V tomto příkladu se `OleDbConnection` objekt používá pro připojení ke zdroji dat, což je `Access MDB` soubor, který je uveden v připojovacím řetězci. Po navázání spojení se vytvoří objekt `OleDbDataAdapter`. Objekt `OleDbDataAdapter` spustí příkaz SELECT jazyk SQL (Structured Query Language) (SQL) pro načtení sady záznamů z databáze. Výsledky z příkazu SQL jsou uloženy v `DataTable` `DataSet` voláním metody `Fill` `OleDbDataAdapter`. `DataTable` v tomto příkladu se jmenuje `BookTable`. Příklad poté nastaví vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> na objekt `DataSet`.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> pak můžeme navazovat na `BookTable` `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` je <xref:System.Windows.DataTemplate> definující způsob zobrazení dat:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` převede `int` na barvu. Při použití tohoto převaděče se barva <xref:System.Windows.Controls.TextBlock.Background%2A> třetího <xref:System.Windows.Controls.TextBlock> zobrazí zelenou, pokud je hodnota `NumPages` menší než 350 a červená v opačném případě. Zde se nezobrazuje implementace převaděče.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.BindingListCollectionView>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
