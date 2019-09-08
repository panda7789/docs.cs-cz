---
title: 'Příklady syntaxe dotazů založených na volání metody: Projekce (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 6617531c8a236eb034e6a063b7a1530c02d6e37b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794806"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="91cf4-102">Příklady syntaxe dotazů založených na volání metody: Projekce (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="91cf4-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>
<span data-ttu-id="91cf4-103">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.Select%2A> metody a <xref:System.Linq.Enumerable.SelectMany%2A> k dotazování <xref:System.Data.DataSet> pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="91cf4-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="91cf4-104">Metoda použitá v těchto příkladech je určena při [načítání dat do datové sady.](loading-data-into-a-dataset.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="91cf4-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="91cf4-105">V příkladech v tomto tématu se používá tabulka Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="91cf4-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="91cf4-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="91cf4-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="91cf4-107">Další informace najdete v tématu [jak: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="91cf4-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="91cf4-108">Vyberte</span><span class="sxs-lookup"><span data-stu-id="91cf4-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="91cf4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="91cf4-109">Example</span></span>  
 <span data-ttu-id="91cf4-110">Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> metodu pro `Name`projektování vlastností, `ProductNumber`a `ListPrice` pro sekvenci anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="91cf4-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="91cf4-111">Vlastnost je také přejmenována `Price` na ve výsledném typu. `ListPrice`</span><span class="sxs-lookup"><span data-stu-id="91cf4-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="91cf4-112">Operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="91cf4-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="91cf4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="91cf4-113">Example</span></span>  
 <span data-ttu-id="91cf4-114">Tento příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde `TotalDue` je méně než 500,00.</span><span class="sxs-lookup"><span data-stu-id="91cf4-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="91cf4-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="91cf4-115">Example</span></span>  
 <span data-ttu-id="91cf4-116">Tento příklad používá <xref:System.Linq.Enumerable.SelectMany%2A> metodu pro výběr všech objednávek, kde byla objednávka vytvořena od 1. října 2002 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="91cf4-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="91cf4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91cf4-117">See also</span></span>

- [<span data-ttu-id="91cf4-118">Načtení dat do datové sady</span><span class="sxs-lookup"><span data-stu-id="91cf4-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="91cf4-119">Příklady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="91cf4-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="91cf4-120">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="91cf4-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="91cf4-121">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91cf4-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
