---
title: 'Příklady syntaxe dotazu na základě metod: Operátory spojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: a77a58d28c667e5dabf0dda4c8d2f4782ea83572
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="7fa9f-102">Příklady syntaxe dotazu na základě metod: Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="7fa9f-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="7fa9f-103">V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="7fa9f-104">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7fa9f-105">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="7fa9f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="7fa9f-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="7fa9f-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="7fa9f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa9f-107">Example</span></span>  
 <span data-ttu-id="7fa9f-108">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky najít číslo objednávky každého zákazníka.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="7fa9f-109">Připojení skupiny je ekvivalentem levé vnější spojení, která vrátí hodnotu každý prvek první zdroje dat (levém), i když žádné korelační elementy jsou v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="7fa9f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa9f-110">Example</span></span>  
 <span data-ttu-id="7fa9f-111">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes tabulky kontaktů a SalesOrderHeader najít číslo objednávky za kontakt.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="7fa9f-112">Zobrazí se počet pořadí a identifikátory pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="7fa9f-113">Join</span><span class="sxs-lookup"><span data-stu-id="7fa9f-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="7fa9f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa9f-114">Example</span></span>  
 <span data-ttu-id="7fa9f-115">Následující příklad spojí přes kontaktu a SalesOrderHeader tabulky.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="7fa9f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa9f-116">Example</span></span>  
 <span data-ttu-id="7fa9f-117">Následující příklad spojí přes kontakt a obraťte se na tabulky SalesOrderHeader, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="7fa9f-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7fa9f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fa9f-118">See Also</span></span>  
 [<span data-ttu-id="7fa9f-119">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7fa9f-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
