---
title: 'Postupy: Provedení dotazu, který vrátí výsledky typu PrimitiveType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: a00448f1c521d468db4cdaa957f92772194c8b43
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854880"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="a09c1-102">Postupy: Provedení dotazu, který vrátí výsledky typu PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="a09c1-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>
<span data-ttu-id="a09c1-103">Toto téma ukazuje <xref:System.Data.EntityClient.EntityCommand>, jak spustit příkaz pro koncepční model pomocí a jak <xref:System.Data.Metadata.Edm.PrimitiveType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a09c1-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="a09c1-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="a09c1-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="a09c1-105">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a09c1-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="a09c1-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="a09c1-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a09c1-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="a09c1-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="a09c1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a09c1-108">Example</span></span>  
 <span data-ttu-id="a09c1-109">Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.PrimitiveType> výsledek.</span><span class="sxs-lookup"><span data-stu-id="a09c1-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="a09c1-110">Pokud předáte následující dotaz jako argument `ExecutePrimitiveTypeQuery` funkci, funkce zobrazí průměrnou Ceník všech: `Products`</span><span class="sxs-lookup"><span data-stu-id="a09c1-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="a09c1-111">Pokud předáte parametrizovaný dotaz, podobně jako následující, <xref:System.Data.EntityClient.EntityParameter> objekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> na vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="a09c1-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="a09c1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a09c1-112">See also</span></span>

- [<span data-ttu-id="a09c1-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a09c1-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a09c1-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a09c1-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
