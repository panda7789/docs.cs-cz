---
title: Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 27a48b7ffe5466c52f19f15cf3c1a6cb558028b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607017"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="33f35-102">Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="33f35-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="33f35-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda a <xref:System.Data.DataRowComparer> třídy.</span><span class="sxs-lookup"><span data-stu-id="33f35-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="33f35-104">`FillDataSet` Metodu použitou v těchto příkladech je zadán v [načítání dat do datová sada](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="33f35-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="33f35-105">Příklady v tomto tématu použijte tabulky Kontakt, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="33f35-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="33f35-106">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="33f35-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="33f35-107">Další informace najdete v tématu [jak: Vytvoření LINQ to DataSet projektu v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="33f35-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="33f35-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="33f35-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="33f35-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="33f35-109">Example</span></span>  
 <span data-ttu-id="33f35-110">Tento příklad načte <xref:System.Data.DataTable> s výsledky dotazu pomocí <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="33f35-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="33f35-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="33f35-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="33f35-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="33f35-112">Example</span></span>  
 <span data-ttu-id="33f35-113">Tento příklad porovná dva řádky s různými daty pomocí <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="33f35-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="33f35-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33f35-114">See also</span></span>

- [<span data-ttu-id="33f35-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="33f35-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="33f35-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="33f35-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
