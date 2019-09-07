---
title: 'Příklady syntaxe výrazů dotazů: Operátory spojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: b1a85dda5d860445174a46d1bc4738962d588369
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398453"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="dd9fb-102">Příklady syntaxe výrazů dotazů: Operátory spojení</span><span class="sxs-lookup"><span data-stu-id="dd9fb-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="dd9fb-103">Spojování je důležitou operací v dotazech, které cílí na zdroje dat, které nemají žádné vztahy naviguje, například tabulky relačních databází.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="dd9fb-104">Spojení dvou zdrojů dat je přidružení objektů v jednom zdroji dat s objekty, které sdílejí společný atribut v jiném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="dd9fb-105">Další informace najdete v tématu [Přehled standardních operátorů dotazů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="dd9fb-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="dd9fb-106">Příklady v tomto tématu ukazují, jak použít <xref:System.Linq.Enumerable.GroupJoin%2A> metody a <xref:System.Linq.Enumerable.Join%2A> k dotazování [modelu prodeje AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="dd9fb-107">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dd9fb-108">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="dd9fb-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="dd9fb-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="dd9fb-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="dd9fb-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd9fb-110">Example</span></span>  
 <span data-ttu-id="dd9fb-111">Následující příklad provede <xref:System.Linq.Enumerable.GroupJoin%2A> v tabulkách SalesOrderHeader a SalesOrderDetail, aby našli počet objednávek na zákazníka.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="dd9fb-112">Spojení se skupinou je ekvivalentem levého vnějšího spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že v jiném zdroji dat nejsou žádné korelační prvky.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="dd9fb-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd9fb-113">Example</span></span>  
 <span data-ttu-id="dd9fb-114">Následující příklad provede <xref:System.Linq.Enumerable.GroupJoin%2A> tabulku Contacts a SalesOrderHeader k vyhledání počtu objednávek na kontakt.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="dd9fb-115">Zobrazí se počet objednávek a ID jednotlivých kontaktů.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="dd9fb-116">Join</span><span class="sxs-lookup"><span data-stu-id="dd9fb-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="dd9fb-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd9fb-117">Example</span></span>  
 <span data-ttu-id="dd9fb-118">Následující příklad provádí spojení s tabulkami SalesOrderHeader a SalesOrderDetail za účelem získání online objednávek z měsíce srpna.</span><span class="sxs-lookup"><span data-stu-id="dd9fb-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="dd9fb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd9fb-119">See also</span></span>

- [<span data-ttu-id="dd9fb-120">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="dd9fb-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
