---
title: Řazení a filtrování dat ADO.NET pomocí součásti BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742974"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="f1da1-102">Postupy: Řazení a filtrování dat ADO.NET pomocí součásti Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="f1da1-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="f1da1-103">Pomocí vlastností <xref:System.Windows.Forms.BindingSource.Sort%2A> a <xref:System.Windows.Forms.BindingSource.Filter%2A> můžete vystavit možnosti řazení a filtrování <xref:System.Windows.Forms.BindingSource> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f1da1-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="f1da1-104">Jednoduché řazení můžete použít, když je podkladový zdroj dat <xref:System.ComponentModel.IBindingList>a můžete použít filtrování a rozšířené řazení, pokud je zdrojem dat <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="f1da1-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="f1da1-105">Vlastnost <xref:System.Windows.Forms.BindingSource.Sort%2A> vyžaduje standardní syntaxi ADO.NET: řetězec představující název sloupce dat ve zdroji dat následovaný `ASC` nebo `DESC` k označení, zda má být seznam seřazen ve vzestupném nebo sestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f1da1-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="f1da1-106">Můžete nastavit pokročilé řazení nebo řazení více sloupců tím, že každý sloupec oddělíte oddělovačem čárky.</span><span class="sxs-lookup"><span data-stu-id="f1da1-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="f1da1-107">Vlastnost <xref:System.Windows.Forms.BindingSource.Filter%2A> přijímá řetězcový výraz.</span><span class="sxs-lookup"><span data-stu-id="f1da1-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1da1-108">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1da1-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="f1da1-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="f1da1-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="f1da1-110">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="f1da1-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="f1da1-111">Filtrování dat pomocí objektu BindingSource</span><span class="sxs-lookup"><span data-stu-id="f1da1-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="f1da1-112">Vlastnost <xref:System.Windows.Forms.BindingSource.Filter%2A> nastavte na výraz, který chcete.</span><span class="sxs-lookup"><span data-stu-id="f1da1-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="f1da1-113">V následujícím příkladu kódu je výraz název sloupce následovaný hodnotou, kterou chcete pro sloupec.</span><span class="sxs-lookup"><span data-stu-id="f1da1-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="f1da1-114">Řazení dat pomocí objektu BindingSource</span><span class="sxs-lookup"><span data-stu-id="f1da1-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="f1da1-115">Vlastnost <xref:System.Windows.Forms.BindingSource.Sort%2A> nastavte na název sloupce, který požadujete, a za ním `ASC` nebo `DESC` určete vzestupné nebo sestupné pořadí.</span><span class="sxs-lookup"><span data-stu-id="f1da1-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="f1da1-116">Oddělte více sloupců čárkou.</span><span class="sxs-lookup"><span data-stu-id="f1da1-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f1da1-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1da1-117">Example</span></span>  
 <span data-ttu-id="f1da1-118">Následující příklad kódu načte data z tabulky Customers ukázkové databáze Northwind do ovládacího prvku <xref:System.Windows.Forms.DataGridView> a filtruje a seřadí zobrazená data.</span><span class="sxs-lookup"><span data-stu-id="f1da1-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1da1-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f1da1-119">Compiling the Code</span></span>  
 <span data-ttu-id="f1da1-120">Chcete-li spustit tento příklad, vložte kód do formuláře obsahujícího <xref:System.Windows.Forms.BindingSource> s názvem `BindingSource1` a <xref:System.Windows.Forms.DataGridView> s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f1da1-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="f1da1-121">Zpracujte událost <xref:System.Windows.Forms.Form.Load> pro formulář a volejte `InitializeSortedFilteredBindingSource` v metodě obslužné rutiny události Load.</span><span class="sxs-lookup"><span data-stu-id="f1da1-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1da1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1da1-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="f1da1-123">[Postupy: Instalace ukázkových databází](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f1da1-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="f1da1-124">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="f1da1-124">BindingSource Component</span></span>](bindingsource-component.md)
