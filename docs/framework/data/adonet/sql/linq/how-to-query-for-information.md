---
title: 'Postupy: dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ae369cb6aaabfdf116f43629a0acb4ad9f7af8c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361249"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="88b89-102">Postupy: dotaz na informace</span><span class="sxs-lookup"><span data-stu-id="88b89-102">How to: Query for Information</span></span>
<span data-ttu-id="88b89-103">Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používají stejnou syntaxi jako dotazy v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88b89-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="88b89-104">Jediným rozdílem je, že objekty odkazovaný ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou namapované na elementy v databázi.</span><span class="sxs-lookup"><span data-stu-id="88b89-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="88b89-105">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="88b89-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="88b89-106"> Přeloží dotazy, které můžete psát na ekvivalentní dotazy SQL a odešle je server pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="88b89-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="88b89-107">Některé funkce [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazy může být nutné zvláštní pozornost v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="88b89-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="88b89-108">Další informace najdete v tématu [dotazu koncepty](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="88b89-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b89-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="88b89-109">Example</span></span>  
 <span data-ttu-id="88b89-110">Následující dotaz zobrazí seznam zákazníky z Londýna.</span><span class="sxs-lookup"><span data-stu-id="88b89-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="88b89-111">V tomto příkladu `Customers` je tabulky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="88b89-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="88b89-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="88b89-112">See Also</span></span>  
 [<span data-ttu-id="88b89-113">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="88b89-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="88b89-114">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="88b89-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="88b89-115">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="88b89-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
