---
title: 'Příklady syntaxe výrazů dotazů: Join Operators'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 3384eb98c8e58563f879b55054077ef801c0ebc7
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827965"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="e65fe-102">Příklady syntaxe výrazů dotazů: Join Operators</span><span class="sxs-lookup"><span data-stu-id="e65fe-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="e65fe-103">Připojení je důležité operace v dotazech, které se zaměřují zdroje dat, které jste žádné relace navigaci k sobě navzájem, jako je například tabulek relační databáze.</span><span class="sxs-lookup"><span data-stu-id="e65fe-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="e65fe-104">Přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat. je spojení dvou datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e65fe-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="e65fe-105">Další informace najdete v tématu [přehled standardních operátorů dotazu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="e65fe-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="e65fe-106">Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e65fe-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="e65fe-107">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e65fe-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e65fe-108">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e65fe-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="e65fe-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="e65fe-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="e65fe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e65fe-110">Example</span></span>  
 <span data-ttu-id="e65fe-111">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky a vyhledá počet objednávek pro zákazníka.</span><span class="sxs-lookup"><span data-stu-id="e65fe-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="e65fe-112">Spojení skupiny je ekvivalentem levé vnější spojení, která vrátí všechny prvky objektu prvního zdroje dat (levý) i v případě, že žádné korelační prvky jsou ve zdroji dat jiné.</span><span class="sxs-lookup"><span data-stu-id="e65fe-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="e65fe-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e65fe-113">Example</span></span>  
 <span data-ttu-id="e65fe-114">Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes kontaktní údaje a SalesOrderHeader tabulky a vyhledá počet objednávek za kontakt.</span><span class="sxs-lookup"><span data-stu-id="e65fe-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="e65fe-115">Zobrazí se počet objednávek a ID každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="e65fe-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="e65fe-116">Join</span><span class="sxs-lookup"><span data-stu-id="e65fe-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="e65fe-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e65fe-117">Example</span></span>  
 <span data-ttu-id="e65fe-118">Následující příklad provádí spojení tabulek SalesOrderHeader a podrobnosti prodejní objednávky získat online objednávky v srpnu.</span><span class="sxs-lookup"><span data-stu-id="e65fe-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="e65fe-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e65fe-119">See also</span></span>
- [<span data-ttu-id="e65fe-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e65fe-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
