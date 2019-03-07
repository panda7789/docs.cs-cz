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
ms.openlocfilehash: 08933e67c2cc4b7ccfb6ae0c9dfde34f40e4e5f5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465543"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="21aad-102">Postupy: Připojení ke zdroji dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="21aad-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="21aad-103">Tento příklad ukazuje, jak vytvořit vazbu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> ovládací prvek [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="21aad-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="21aad-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="21aad-104">Example</span></span>

<span data-ttu-id="21aad-105">V tomto příkladu `OleDbConnection` objektu se používá k připojení ke zdroji dat, která je `Access MDB` soubor, který je zadán v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="21aad-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="21aad-106">Po navázání připojení `OleDbDataAdapter` je vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="21aad-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="21aad-107">`OleDbDataAdapter` Objektu provede s výběrem [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] příkazem pro načtení záznamů z databáze.</span><span class="sxs-lookup"><span data-stu-id="21aad-107">The `OleDbDataAdapter` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="21aad-108">Výsledky z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] příkazu jsou uložené v `DataTable` z `DataSet` voláním `Fill` metodu `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="21aad-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="21aad-109">`DataTable` v tomto příkladu je pojmenována `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="21aad-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="21aad-110">Příklad poté nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `DataSet` objektu.</span><span class="sxs-lookup"><span data-stu-id="21aad-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="21aad-111">Potom jsme mohl vytvořit vazbu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox> k `BookTable` z `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="21aad-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="21aad-112">`BookItemTemplate` je <xref:System.Windows.DataTemplate> , který definuje, jak se data zobrazí:</span><span class="sxs-lookup"><span data-stu-id="21aad-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="21aad-113">`IntColorConverter` Převede `int` na barvu.</span><span class="sxs-lookup"><span data-stu-id="21aad-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="21aad-114">Pomocí tohoto převaděče <xref:System.Windows.Controls.TextBlock.Background%2A> barva třetí <xref:System.Windows.Controls.TextBlock> zobrazí zeleně Pokud hodnota `NumPages` jinak je menší než 350 a červenou.</span><span class="sxs-lookup"><span data-stu-id="21aad-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="21aad-115">Implementace konvertoru zde není zobrazen.</span><span class="sxs-lookup"><span data-stu-id="21aad-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="21aad-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21aad-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="21aad-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="21aad-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="21aad-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="21aad-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
