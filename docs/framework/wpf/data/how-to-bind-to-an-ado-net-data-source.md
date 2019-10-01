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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="e0a2d-102">Postupy: Připojení ke zdroji dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e0a2d-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="e0a2d-103">Tento příklad ukazuje, jak navazovat ovládací prvek [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> na ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="e0a2d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0a2d-104">Example</span></span>

<span data-ttu-id="e0a2d-105">V tomto příkladu je objekt `OleDbConnection` použit pro připojení ke zdroji dat, který je soubor `Access MDB`, který je uveden v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="e0a2d-106">Po navázání spojení se vytvoří objekt `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="e0a2d-107">Objekt `OleDbDataAdapter` spustí příkaz SELECT jazyk SQL (Structured Query Language) (SQL) pro načtení sady záznamů z databáze.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="e0a2d-108">Výsledky z příkazu SQL jsou uloženy v `DataTable` `DataSet` voláním metody `Fill` `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="e0a2d-109">@No__t-0 v tomto příkladu je pojmenován `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="e0a2d-110">Příklad potom nastaví vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.ListBox> na objekt `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="e0a2d-111">Potom můžeme Navazovat vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> na `BookTable` `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="e0a2d-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="e0a2d-112">`BookItemTemplate` je <xref:System.Windows.DataTemplate> definující způsob zobrazení dat:</span><span class="sxs-lookup"><span data-stu-id="e0a2d-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="e0a2d-113">@No__t-0 převede `int` na barvu.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="e0a2d-114">Při použití tohoto převaděče se barva <xref:System.Windows.Controls.TextBlock.Background%2A> třetího <xref:System.Windows.Controls.TextBlock> zobrazí zelenou, pokud je hodnota `NumPages` menší než 350 a červená, jinak.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="e0a2d-115">Zde se nezobrazuje implementace převaděče.</span><span class="sxs-lookup"><span data-stu-id="e0a2d-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0a2d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0a2d-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="e0a2d-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="e0a2d-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e0a2d-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="e0a2d-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
