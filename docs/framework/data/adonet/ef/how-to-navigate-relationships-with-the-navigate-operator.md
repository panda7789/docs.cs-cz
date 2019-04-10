---
title: 'Postupy: Procházení relací pomocí navigačního operátoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 94789bcc007056a26d206903dc554ffe35999823
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322326"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="8355f-102">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="8355f-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="8355f-103">Toto téma ukazuje, jak provést příkaz pro koncepční model s použitím <xref:System.Data.EntityClient.EntityCommand> objekt a jak načíst <xref:System.Data.Metadata.Edm.RefType> výsledky s použitím <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8355f-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="8355f-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="8355f-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="8355f-105">Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8355f-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8355f-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8355f-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="8355f-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="8355f-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="8355f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8355f-108">Example</span></span>  
 <span data-ttu-id="8355f-109">Následující příklad ukazuje, jak procházení vztahů v [!INCLUDE[esql](../../../../../includes/esql-md.md)] pomocí [NAVIGOVAT](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="8355f-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="8355f-110">`Navigate` Operátor používá následující parametry: instance entity, typ vztahu, end relace a zahájení relace.</span><span class="sxs-lookup"><span data-stu-id="8355f-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="8355f-111">Volitelně můžete předat pouze instance entitu a typ vztahu, který má `Navigate` operátor.</span><span class="sxs-lookup"><span data-stu-id="8355f-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="8355f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8355f-112">See also</span></span>

- [<span data-ttu-id="8355f-113">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8355f-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="8355f-114">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8355f-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
