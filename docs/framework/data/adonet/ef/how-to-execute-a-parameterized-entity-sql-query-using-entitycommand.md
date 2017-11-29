---
title: "Postupy: spuštění dotazu SQL parametrizované Entity pomocí objekt EntityCommand"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1531e18a6be3e7ab5c0cec4f19f33692fd04383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="aa6a1-102">Postupy: spuštění dotazu SQL parametrizované Entity pomocí objekt EntityCommand</span><span class="sxs-lookup"><span data-stu-id="aa6a1-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="aa6a1-103">Toto téma ukazuje, jak provést [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který obsahuje parametry pomocí <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="aa6a1-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="aa6a1-104">Spustí kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="aa6a1-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="aa6a1-105">Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa6a1-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="aa6a1-106">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="aa6a1-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="aa6a1-107">Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="aa6a1-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="aa6a1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa6a1-108">Example</span></span>  
 <span data-ttu-id="aa6a1-109">Následující příklad ukazuje, jak vytvořit řetězec dotazu s dva parametry.</span><span class="sxs-lookup"><span data-stu-id="aa6a1-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="aa6a1-110">Ta poté vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry k <xref:System.Data.EntityClient.EntityParameter> kolekci této <xref:System.Data.EntityClient.EntityCommand>a provádí iteraci v kolekci z `Contact` položky.</span><span class="sxs-lookup"><span data-stu-id="aa6a1-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="aa6a1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa6a1-111">See Also</span></span>  
 [<span data-ttu-id="aa6a1-112">Postup: provedení parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="aa6a1-112">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [<span data-ttu-id="aa6a1-113">Jazyk SQL entity</span><span class="sxs-lookup"><span data-stu-id="aa6a1-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
