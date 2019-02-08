---
title: 'Postupy: Provedení dotazu, který vrátí vnořené kolekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 466187bf340d8cc2088615ae942131658399d65f
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827094"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="8d749-102">Postupy: Provedení dotazu, který vrátí vnořené kolekce</span><span class="sxs-lookup"><span data-stu-id="8d749-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="8d749-103">To ukazuje, jak provést příkaz pro koncepční model s použitím <xref:System.Data.EntityClient.EntityCommand> objekt a jak načíst výsledky vnořené kolekce s použitím <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8d749-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="8d749-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="8d749-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="8d749-105">Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d749-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8d749-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8d749-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="8d749-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="8d749-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="8d749-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d749-108">Example</span></span>  
 <span data-ttu-id="8d749-109">A *vnořené kolekce* je kolekce, která se nachází uvnitř jiné kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d749-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="8d749-110">Následující kód načte kolekci `Contacts` a vnořené kolekce `SalesOrderHeaders` , které jsou spojeny s každým `Contact`.</span><span class="sxs-lookup"><span data-stu-id="8d749-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="8d749-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d749-111">See also</span></span>
- [<span data-ttu-id="8d749-112">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8d749-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
