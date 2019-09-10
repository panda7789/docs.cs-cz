---
title: 'Postupy: Provedení dotazu, který vrátí výsledky typu RefType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: c9f3b7e19770c89bbb200913bf7fcf44f901ea99
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854573"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="ee5ff-102">Postupy: Provedení dotazu, který vrátí výsledky typu RefType</span><span class="sxs-lookup"><span data-stu-id="ee5ff-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="ee5ff-103">Toto téma ukazuje, jak spustit příkaz pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objektu a jak <xref:System.Data.Metadata.Edm.RefType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ee5ff-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="ee5ff-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ee5ff-105">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ee5ff-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="ee5ff-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ee5ff-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ee5ff-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ee5ff-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee5ff-108">Example</span></span>  
 <span data-ttu-id="ee5ff-109">Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.RefType> výsledky.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="ee5ff-110">Pokud předáte následující dotaz jako argument `ExecuteRefTypeQuery` funkci, vrátí funkce odkaz na entitu:</span><span class="sxs-lookup"><span data-stu-id="ee5ff-110">If you pass the following query as an argument to the `ExecuteRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="ee5ff-111">Pokud předáte parametrizovaný dotaz, podobně jako následující, přidejte <xref:System.Data.EntityClient.EntityParameter> objekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> do vlastnosti <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="ee5ff-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee5ff-112">See also</span></span>

- [<span data-ttu-id="ee5ff-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ee5ff-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="ee5ff-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ee5ff-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
