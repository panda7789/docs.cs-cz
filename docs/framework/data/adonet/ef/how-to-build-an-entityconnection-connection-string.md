---
title: "Postupy: sestavení řetězec připojení EntityConnection"
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
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fcfba15112c59a1985adb25d164bfea0e434f7b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="e0fad-102">Postupy: sestavení řetězec připojení EntityConnection</span><span class="sxs-lookup"><span data-stu-id="e0fad-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="e0fad-103">Toto téma představuje příklad, jak sestavit <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="e0fad-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e0fad-104">Spustí kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="e0fad-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="e0fad-105">Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0fad-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="e0fad-106">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="e0fad-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="e0fad-107">Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="e0fad-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="e0fad-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0fad-108">Example</span></span>  
 <span data-ttu-id="e0fad-109">Tento příklad inicializuje <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> pro výchozí zprostředkovatel, pak inicializuje <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> objektu a předá tento objekt do konstruktoru objektu <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="e0fad-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="e0fad-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0fad-110">See Also</span></span>  
 [<span data-ttu-id="e0fad-111">Postupy: použití EntityConnection s kontextu objektu</span><span class="sxs-lookup"><span data-stu-id="e0fad-111">How to: Use EntityConnection with an Object Context</span></span>](http://msdn.microsoft.com/en-us/2140fe7b-b88b-47c8-a749-d7f142eb1080)  
 [<span data-ttu-id="e0fad-112">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="e0fad-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
