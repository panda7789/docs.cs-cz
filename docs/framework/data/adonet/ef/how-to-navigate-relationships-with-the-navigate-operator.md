---
title: "Postupy: procházení vztahů pomocí přejděte – operátor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38b2a6630d967519f3c907c60944d943c6b9b720
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="5d5ba-102">Postupy: procházení vztahů pomocí přejděte – operátor</span><span class="sxs-lookup"><span data-stu-id="5d5ba-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="5d5ba-103">Toto téma ukazuje, jak k provedení příkazu pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objekt a jak načíst <xref:System.Data.Metadata.Edm.RefType> výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="5d5ba-104">Spustí kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="5d5ba-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="5d5ba-105">Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d5ba-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5d5ba-106">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="5d5ba-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="5d5ba-107">Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="5d5ba-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="5d5ba-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d5ba-108">Example</span></span>  
 <span data-ttu-id="5d5ba-109">Následující příklad ukazuje, jak se orientovat vztahy v [!INCLUDE[esql](../../../../../includes/esql-md.md)] pomocí [přejděte](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="5d5ba-110">`Navigate` Operátor mají následující parametry: instanci entity, typ vztahu, konec relace a začátku relace.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="5d5ba-111">Volitelně můžete předat pouze instanci entity a typ relace, který má `Navigate` operátor.</span><span class="sxs-lookup"><span data-stu-id="5d5ba-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="5d5ba-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d5ba-112">See Also</span></span>  
 [<span data-ttu-id="5d5ba-113">Zprostředkovatel EntityClient rozhraní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5d5ba-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="5d5ba-114">Jazyk SQL entity</span><span class="sxs-lookup"><span data-stu-id="5d5ba-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
