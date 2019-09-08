---
title: 'Postupy: Dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793533"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="b5f22-102">Postupy: Dotaz na informace</span><span class="sxs-lookup"><span data-stu-id="b5f22-102">How to: Query for Information</span></span>
<span data-ttu-id="b5f22-103">Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji používají stejnou syntaxi jako dotazy v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f22-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="b5f22-104">Jediným rozdílem je, že objekty odkazované v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazech jsou mapovány na prvky v databázi.</span><span class="sxs-lookup"><span data-stu-id="b5f22-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="b5f22-105">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b5f22-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b5f22-106">přeloží dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="b5f22-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="b5f22-107">Některé funkce [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazů můžou v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacích vyžadovat zvláštní pozornost.</span><span class="sxs-lookup"><span data-stu-id="b5f22-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="b5f22-108">Další informace najdete v tématu [Koncepty dotazů](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="b5f22-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f22-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5f22-109">Example</span></span>  
 <span data-ttu-id="b5f22-110">Následující dotaz požádá o seznam zákazníků z Londýna.</span><span class="sxs-lookup"><span data-stu-id="b5f22-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="b5f22-111">V tomto příkladu `Customers` je tabulka v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="b5f22-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b5f22-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5f22-112">See also</span></span>

- [<span data-ttu-id="b5f22-113">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="b5f22-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="b5f22-114">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="b5f22-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="b5f22-115">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="b5f22-115">Querying the Database</span></span>](querying-the-database.md)
