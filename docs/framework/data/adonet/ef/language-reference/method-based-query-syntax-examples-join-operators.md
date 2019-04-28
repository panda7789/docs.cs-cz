---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory spojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 700c29222d10177774e118e53fb51f177b723679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760529"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="77de3-102">Příklady syntaxe dotazů založených na volání metody: Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="77de3-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="77de3-103">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe dotazů založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="77de3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="77de3-104">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="77de3-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="77de3-105">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="77de3-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="77de3-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="77de3-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="77de3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="77de3-107">Example</span></span>  
 <span data-ttu-id="77de3-108">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky a vyhledá počet objednávek pro zákazníka.</span><span class="sxs-lookup"><span data-stu-id="77de3-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="77de3-109">Spojení skupiny je ekvivalentem levé vnější spojení, která vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že žádné korelační prvky jsou ve zdroji dat jiné.</span><span class="sxs-lookup"><span data-stu-id="77de3-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="77de3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="77de3-110">Example</span></span>  
 <span data-ttu-id="77de3-111">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes kontaktní údaje a SalesOrderHeader tabulky a vyhledá počet objednávek za kontakt.</span><span class="sxs-lookup"><span data-stu-id="77de3-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="77de3-112">Zobrazí se počet objednávek a ID každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="77de3-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="77de3-113">Join</span><span class="sxs-lookup"><span data-stu-id="77de3-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="77de3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="77de3-114">Example</span></span>  
 <span data-ttu-id="77de3-115">Následující příklad provádí spojení kontaktní údaje a SalesOrderHeader tabulky.</span><span class="sxs-lookup"><span data-stu-id="77de3-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="77de3-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="77de3-116">Example</span></span>  
 <span data-ttu-id="77de3-117">Následující příklad provádí spojení kontaktu a obraťte se na tabulky SalesOrderHeader, seskupení výsledků podle ID.</span><span class="sxs-lookup"><span data-stu-id="77de3-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="77de3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77de3-118">See also</span></span>

- [<span data-ttu-id="77de3-119">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="77de3-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
