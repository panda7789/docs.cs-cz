---
title: 'Postupy: provedení dotazu, který vrátí výsledky typu RefType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: 96e4034c6a2476e1dfcf8e8ef22bae6e5b8d4934
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469801"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="d1c2a-102">Postupy: provedení dotazu, který vrátí výsledky typu RefType</span><span class="sxs-lookup"><span data-stu-id="d1c2a-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="d1c2a-103">Toto téma ukazuje, jak provést příkaz pro koncepční model s použitím <xref:System.Data.EntityClient.EntityCommand> objekt a jak načíst <xref:System.Data.Metadata.Edm.RefType> výsledky s použitím <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d1c2a-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d1c2a-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="d1c2a-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="d1c2a-105">Přidat [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1c2a-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="d1c2a-106">Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="d1c2a-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="d1c2a-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d1c2a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="d1c2a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1c2a-108">Example</span></span>  
 <span data-ttu-id="d1c2a-109">Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.RefType> výsledky.</span><span class="sxs-lookup"><span data-stu-id="d1c2a-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="d1c2a-110">Pokud je předat jako argument pro následující dotaz `ExectueRefTypeQuery` funkce, funkce vrátí odkaz na entitu:</span><span class="sxs-lookup"><span data-stu-id="d1c2a-110">If you pass the following query as an argument to the `ExectueRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="d1c2a-111">Pokud předáte parametrický dotaz, následujícím postupem, přidejte <xref:System.Data.EntityClient.EntityParameter> objektů <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="d1c2a-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="d1c2a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1c2a-112">See Also</span></span>  
 [<span data-ttu-id="d1c2a-113">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d1c2a-113">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d1c2a-114">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d1c2a-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
