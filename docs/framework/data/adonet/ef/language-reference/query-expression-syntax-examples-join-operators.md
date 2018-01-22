---
title: "Příklady syntaxe výrazu dotazu: Operátory spojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bea82d01c2eea5e9aa892f9ab7cee95944329849
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="8528d-102">Příklady syntaxe výrazu dotazu: Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="8528d-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="8528d-103">Připojení je důležité operace v dotazech, které cílí zdrojů dat, které nemají žádné navigaci relace mezi sebou, jako jsou tabulky relační databáze.</span><span class="sxs-lookup"><span data-stu-id="8528d-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="8528d-104">Spojení dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="8528d-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="8528d-105">Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="8528d-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="8528d-106">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="8528d-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="8528d-107">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8528d-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8528d-108">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="8528d-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="8528d-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="8528d-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="8528d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8528d-110">Example</span></span>  
 <span data-ttu-id="8528d-111">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky najít číslo objednávky každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="8528d-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="8528d-112">Připojení skupiny je ekvivalentem levé vnější spojení, která vrátí hodnotu každý prvek první zdroje dat (levém), i když žádné korelační elementy jsou v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="8528d-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="8528d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8528d-113">Example</span></span>  
 <span data-ttu-id="8528d-114">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes tabulky kontaktů a SalesOrderHeader najít číslo objednávky za kontakt.</span><span class="sxs-lookup"><span data-stu-id="8528d-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="8528d-115">Zobrazí se počet pořadí a identifikátory pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="8528d-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a><span data-ttu-id="8528d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8528d-116">Example</span></span>  
 <span data-ttu-id="8528d-117">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes kontaktu a SalesOrderHeader tabulky.</span><span class="sxs-lookup"><span data-stu-id="8528d-117">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables.</span></span> <span data-ttu-id="8528d-118">Připojení skupiny je ekvivalentem levé vnější spojení, která vrátí hodnotu každý prvek první zdroje dat (levém), i když žádné korelační elementy jsou v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="8528d-118">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="8528d-119">Join</span><span class="sxs-lookup"><span data-stu-id="8528d-119">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="8528d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8528d-120">Example</span></span>  
 <span data-ttu-id="8528d-121">Následující příklad spojí přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky, které chcete získat online objednávky z srpnu.</span><span class="sxs-lookup"><span data-stu-id="8528d-121">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="8528d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8528d-122">See Also</span></span>  
 [<span data-ttu-id="8528d-123">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8528d-123">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
