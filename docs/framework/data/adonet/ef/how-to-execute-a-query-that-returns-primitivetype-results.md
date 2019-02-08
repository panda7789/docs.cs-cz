---
title: 'Postupy: Spustit dotaz, který vrátí výsledky typu PrimitiveType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: 0b8c473171f86b569f42c75701805818d8b81c42
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825768"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="c8083-102">Postupy: Spustit dotaz, který vrátí výsledky typu PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="c8083-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>
<span data-ttu-id="c8083-103">Toto téma ukazuje, jak provést příkaz pro koncepční model s použitím <xref:System.Data.EntityClient.EntityCommand>a jak načíst <xref:System.Data.Metadata.Edm.PrimitiveType> výsledky s použitím <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="c8083-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="c8083-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="c8083-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="c8083-105">Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8083-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="c8083-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c8083-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="c8083-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="c8083-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="c8083-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8083-108">Example</span></span>  
 <span data-ttu-id="c8083-109">Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.PrimitiveType> výsledek.</span><span class="sxs-lookup"><span data-stu-id="c8083-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="c8083-110">Pokud je předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` funkce, funkce zobrazuje průměrnou cenu seznam všech `Products`:</span><span class="sxs-lookup"><span data-stu-id="c8083-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="c8083-111">Pokud předáte parametrizovaného dotazu, jako je následující <xref:System.Data.EntityClient.EntityParameter> objektů <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="c8083-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="c8083-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8083-112">See also</span></span>
- [<span data-ttu-id="c8083-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c8083-113">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="c8083-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c8083-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
