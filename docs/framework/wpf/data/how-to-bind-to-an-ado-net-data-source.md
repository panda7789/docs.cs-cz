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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="8a0a0-102">Postupy: Připojení ke zdroji dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a0a0-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="8a0a0-103">Tento příklad ukazuje, jak vytvořit vazby [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> ovládacího prvku na `DataSet`ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="8a0a0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a0a0-104">Example</span></span>

<span data-ttu-id="8a0a0-105">V tomto příkladu se `OleDbConnection` objekt používá pro připojení ke zdroji dat, což je `Access MDB` soubor, který je uveden v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="8a0a0-106">Po navázání spojení se vytvoří objekt `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="8a0a0-107">Objekt `OleDbDataAdapter` spustí příkaz SELECT jazyk SQL (Structured Query Language) (SQL) pro načtení sady záznamů z databáze.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="8a0a0-108">Výsledky z příkazu SQL jsou uloženy v `DataTable` `DataSet` voláním metody `Fill` `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="8a0a0-109">`DataTable` v tomto příkladu se jmenuje `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="8a0a0-110">Příklad poté nastaví vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> na objekt `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="8a0a0-111">Vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> pak můžeme navazovat na `BookTable` `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="8a0a0-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="8a0a0-112">`BookItemTemplate` je <xref:System.Windows.DataTemplate> definující způsob zobrazení dat:</span><span class="sxs-lookup"><span data-stu-id="8a0a0-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="8a0a0-113">`IntColorConverter` převede `int` na barvu.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="8a0a0-114">Při použití tohoto převaděče se barva <xref:System.Windows.Controls.TextBlock.Background%2A> třetího <xref:System.Windows.Controls.TextBlock> zobrazí zelenou, pokud je hodnota `NumPages` menší než 350 a červená v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="8a0a0-115">Zde se nezobrazuje implementace převaděče.</span><span class="sxs-lookup"><span data-stu-id="8a0a0-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a0a0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a0a0-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="8a0a0-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="8a0a0-117">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="8a0a0-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8a0a0-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
