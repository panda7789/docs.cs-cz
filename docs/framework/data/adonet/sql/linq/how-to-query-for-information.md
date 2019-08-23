---
title: 'Postupy: Dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 2987e43c83bf84e32cd05a870b24da40dd37d8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943558"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="44e93-102">Postupy: Dotaz na informace</span><span class="sxs-lookup"><span data-stu-id="44e93-102">How to: Query for Information</span></span>
<span data-ttu-id="44e93-103">Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji používají stejnou syntaxi jako dotazy v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44e93-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="44e93-104">Jediným rozdílem je, že objekty odkazované v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazech jsou mapovány na prvky v databázi.</span><span class="sxs-lookup"><span data-stu-id="44e93-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="44e93-105">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="44e93-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="44e93-106">přeloží dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="44e93-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="44e93-107">Některé funkce [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazů můžou v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacích vyžadovat zvláštní pozornost.</span><span class="sxs-lookup"><span data-stu-id="44e93-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="44e93-108">Další informace najdete v tématu [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="44e93-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e93-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="44e93-109">Example</span></span>  
 <span data-ttu-id="44e93-110">Následující dotaz požádá o seznam zákazníků z Londýna.</span><span class="sxs-lookup"><span data-stu-id="44e93-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="44e93-111">V tomto příkladu `Customers` je tabulka v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="44e93-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44e93-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44e93-112">See also</span></span>

- [<span data-ttu-id="44e93-113">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="44e93-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="44e93-114">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="44e93-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="44e93-115">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="44e93-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
