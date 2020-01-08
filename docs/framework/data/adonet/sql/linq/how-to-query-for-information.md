---
title: 'Postupy: dotaz na informace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634648"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="f0c44-102">Postupy: dotaz na informace</span><span class="sxs-lookup"><span data-stu-id="f0c44-102">How to: Query for Information</span></span>
<span data-ttu-id="f0c44-103">Dotazy v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používají stejnou syntaxi jako dotazy v LINQ.</span><span class="sxs-lookup"><span data-stu-id="f0c44-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="f0c44-104">Jediným rozdílem je, že objekty odkazované v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy jsou namapovány na prvky v databázi.</span><span class="sxs-lookup"><span data-stu-id="f0c44-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="f0c44-105">Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="f0c44-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f0c44-106">překládá dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="f0c44-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="f0c44-107">Některé funkce dotazů LINQ mohou vyžadovat zvláštní pozornost v aplikacích [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0c44-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="f0c44-108">Další informace najdete v tématu [Koncepty dotazů](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="f0c44-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0c44-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0c44-109">Example</span></span>  
 <span data-ttu-id="f0c44-110">Následující dotaz požádá o seznam zákazníků z Londýna.</span><span class="sxs-lookup"><span data-stu-id="f0c44-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="f0c44-111">V tomto příkladu je `Customers` tabulka v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="f0c44-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f0c44-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0c44-112">See also</span></span>

- [<span data-ttu-id="f0c44-113">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="f0c44-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="f0c44-114">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="f0c44-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="f0c44-115">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="f0c44-115">Querying the Database</span></span>](querying-the-database.md)
