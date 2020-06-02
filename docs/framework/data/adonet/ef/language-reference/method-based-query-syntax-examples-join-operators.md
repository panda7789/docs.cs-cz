---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory spojení'
description: Pomocí těchto příkladů se naučíte používat metody join a GroupJoin k dotazování modelu pomocí syntaxe dotazu založeného na metodách v LINQ to Entities.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 3b1445b39bdcd9a9b4d0672be0598233319cb85d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286828"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="eeb0a-103">Příklady syntaxe dotazů založených na volání metody: Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="eeb0a-103">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="eeb0a-104">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A> metody a k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="eeb0a-105">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="eeb0a-106">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="eeb0a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="eeb0a-107">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="eeb0a-107">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="eeb0a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="eeb0a-108">Example</span></span>  
 <span data-ttu-id="eeb0a-109">Následující příklad provede v <xref:System.Linq.Enumerable.GroupJoin%2A> tabulkách SalesOrderHeader a SalesOrderDetail, aby našli počet objednávek na zákazníka.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-109">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="eeb0a-110">Spojení se skupinou je ekvivalentem levého vnějšího spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že v jiném zdroji dat nejsou žádné korelační prvky.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-110">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="eeb0a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="eeb0a-111">Example</span></span>  
 <span data-ttu-id="eeb0a-112">Následující příklad provede <xref:System.Linq.Enumerable.GroupJoin%2A> tabulku Contacts a SalesOrderHeader k vyhledání počtu objednávek na kontakt.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-112">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="eeb0a-113">Zobrazí se počet objednávek a ID jednotlivých kontaktů.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-113">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="eeb0a-114">Spojit</span><span class="sxs-lookup"><span data-stu-id="eeb0a-114">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="eeb0a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="eeb0a-115">Example</span></span>  
 <span data-ttu-id="eeb0a-116">Následující příklad provádí spojení s tabulkami Contact a SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-116">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="eeb0a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="eeb0a-117">Example</span></span>  
 <span data-ttu-id="eeb0a-118">Následující příklad provádí spojení s tabulkami Contact a SalesOrderHeader a seskupí výsledky podle ID kontaktu.</span><span class="sxs-lookup"><span data-stu-id="eeb0a-118">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="eeb0a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="eeb0a-119">See also</span></span>

- [<span data-ttu-id="eeb0a-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="eeb0a-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
