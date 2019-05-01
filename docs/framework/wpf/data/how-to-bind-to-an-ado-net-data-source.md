---
title: 'Postupy: Vytvoření vazby ke zdroji dat ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 08933e67c2cc4b7ccfb6ae0c9dfde34f40e4e5f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021039"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Postupy: Vytvoření vazby ke zdroji dat ADO.NET

Tento příklad ukazuje, jak vytvořit vazbu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> ovládací prvek [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.

## <a name="example"></a>Příklad

V tomto příkladu `OleDbConnection` objektu se používá k připojení ke zdroji dat, která je `Access MDB` soubor, který je zadán v připojovacím řetězci. Po navázání připojení `OleDbDataAdapter` je vytvořen objekt. `OleDbDataAdapter` Objektu provede s výběrem [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] příkazem pro načtení záznamů z databáze. Výsledky z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] příkazu jsou uložené v `DataTable` z `DataSet` voláním `Fill` metodu `OleDbDataAdapter`. `DataTable` v tomto příkladu je pojmenována `BookTable`. Příklad poté nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `DataSet` objektu.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Potom jsme mohl vytvořit vazbu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `BookTable` z `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` je <xref:System.Windows.DataTemplate> , který definuje, jak se data zobrazí:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` Převede `int` na barvu. Pomocí tohoto převaděče <xref:System.Windows.Controls.TextBlock.Background%2A> barva třetí <xref:System.Windows.Controls.TextBlock> zobrazí zeleně Pokud hodnota `NumPages` jinak je menší než 350 a červenou. Implementace konvertoru zde není zobrazen.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.BindingListCollectionView>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
