---
title: 'Postupy: Procházení relací pomocí navigačního operátoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: dca8c25babcbc1676552af8ef49b7a7e71cd6136
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854525"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="4153b-102">Postupy: Procházení relací pomocí navigačního operátoru</span><span class="sxs-lookup"><span data-stu-id="4153b-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="4153b-103">Toto téma ukazuje, jak spustit příkaz pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objektu a jak <xref:System.Data.Metadata.Edm.RefType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="4153b-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="4153b-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="4153b-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="4153b-105">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4153b-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="4153b-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="4153b-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="4153b-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="4153b-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="4153b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4153b-108">Example</span></span>  
 <span data-ttu-id="4153b-109">Následující příklad ukazuje, jak navigovat relace v [!INCLUDE[esql](../../../../../includes/esql-md.md)] nástroji pomocí operátoru [Navigace](./language-reference/navigate-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="4153b-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](./language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="4153b-110">`Navigate` Operátor přebírá následující parametry: instance entity, typ vztahu, konec relace a začátek relace.</span><span class="sxs-lookup"><span data-stu-id="4153b-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="4153b-111">Volitelně můžete `Navigate` operátorovi předat jenom instanci entity a typ vztahu.</span><span class="sxs-lookup"><span data-stu-id="4153b-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="4153b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4153b-112">See also</span></span>

- [<span data-ttu-id="4153b-113">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4153b-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="4153b-114">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4153b-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
