---
title: 'Příklady syntaxe dotazů metoda: Nastavte operátory (LINQ na DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 2c95125182a352d3cd2b0b4c51ffac3f74fff5a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764811"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="29e23-102">Příklady syntaxe dotazů metoda: Nastavte operátory (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="29e23-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="29e23-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, a <xref:System.Linq.Enumerable.Union%2A> operátory provádět operace porovnání hodnota založená na sady řádků dat.[ Načítání dat do datovou sadu](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) najdete v části [porovnávání DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) Další informace o <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="29e23-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) See [Comparing DataRows](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="29e23-104">`FillDataSet` Metodu použitou v těchto příkladech je uveden v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="29e23-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="29e23-105">V příkladech v tomto tématu použijte kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="29e23-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="29e23-106">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="29e23-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="29e23-107">Další informace najdete v tématu [postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="29e23-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="29e23-108">Distinct</span><span class="sxs-lookup"><span data-stu-id="29e23-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="29e23-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="29e23-109">Example</span></span>  
 <span data-ttu-id="29e23-110">Tento příklad používá <xref:System.Linq.Enumerable.Distinct%2A> metodu odeberte duplicitní elementy v pořadí.</span><span class="sxs-lookup"><span data-stu-id="29e23-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="29e23-111">S výjimkou</span><span class="sxs-lookup"><span data-stu-id="29e23-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="29e23-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="29e23-112">Example</span></span>  
 <span data-ttu-id="29e23-113">Tento příklad používá <xref:System.Linq.Enumerable.Except%2A> metoda vrátí kontakty, které se zobrazují v první tabulce, ale ne za sekundu.</span><span class="sxs-lookup"><span data-stu-id="29e23-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="29e23-114">Intersect</span><span class="sxs-lookup"><span data-stu-id="29e23-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="29e23-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="29e23-115">Example</span></span>  
 <span data-ttu-id="29e23-116">Tento příklad používá <xref:System.Linq.Enumerable.Intersect%2A> metoda vrátí kontakty, které se zobrazují v obou tabulkách.</span><span class="sxs-lookup"><span data-stu-id="29e23-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="29e23-117">Unie</span><span class="sxs-lookup"><span data-stu-id="29e23-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="29e23-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="29e23-118">Example</span></span>  
 <span data-ttu-id="29e23-119">Tento příklad používá <xref:System.Linq.Enumerable.Union%2A> metoda vrátí jedinečný kontakty z kterékoli z obou tabulek.</span><span class="sxs-lookup"><span data-stu-id="29e23-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="29e23-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="29e23-120">See Also</span></span>  
 [<span data-ttu-id="29e23-121">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="29e23-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="29e23-122">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="29e23-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="29e23-123">Přehled standardních operátorů dotazu</span><span class="sxs-lookup"><span data-stu-id="29e23-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
