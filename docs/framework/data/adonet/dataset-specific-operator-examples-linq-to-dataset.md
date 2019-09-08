---
title: Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 6a9dc82e0bb065b455c0208daaf2d28a74cd7e34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784198"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="0129e-102">Příklady operátorů specifických pro datovou sadu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0129e-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="0129e-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodu <xref:System.Data.DataRowComparer> a třídu.</span><span class="sxs-lookup"><span data-stu-id="0129e-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="0129e-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="0129e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0129e-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0129e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0129e-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="0129e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0129e-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0129e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="0129e-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="0129e-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="0129e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0129e-109">Example</span></span>  
 <span data-ttu-id="0129e-110">Tento příklad načte <xref:System.Data.DataTable> s výsledky dotazu <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="0129e-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="0129e-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="0129e-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="0129e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0129e-112">Example</span></span>  
 <span data-ttu-id="0129e-113">Tento příklad porovnává dva různé datové řádky pomocí <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="0129e-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="0129e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0129e-114">See also</span></span>

- [<span data-ttu-id="0129e-115">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="0129e-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0129e-116">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0129e-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
