---
title: 'Postupy: spuštění dotazu SQL parametrizované Entity pomocí objekt EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: c8469f8f13178a09c636d33070fd5ad4cbb912aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="33a30-102">Postupy: spuštění dotazu SQL parametrizované Entity pomocí objekt EntityCommand</span><span class="sxs-lookup"><span data-stu-id="33a30-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="33a30-103">Toto téma ukazuje, jak provést [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který obsahuje parametry pomocí <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="33a30-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="33a30-104">Spustí kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="33a30-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="33a30-105">Přidat [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33a30-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="33a30-106">Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="33a30-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="33a30-107">Na stránce kódu pro aplikace, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="33a30-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="33a30-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="33a30-108">Example</span></span>  
 <span data-ttu-id="33a30-109">Následující příklad ukazuje, jak vytvořit řetězec dotazu s dva parametry.</span><span class="sxs-lookup"><span data-stu-id="33a30-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="33a30-110">Ta poté vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry k <xref:System.Data.EntityClient.EntityParameter> kolekci této <xref:System.Data.EntityClient.EntityCommand>a provádí iteraci v kolekci z `Contact` položky.</span><span class="sxs-lookup"><span data-stu-id="33a30-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="33a30-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="33a30-111">See Also</span></span>  
 [<span data-ttu-id="33a30-112">Postup: provedení parametrizovaného dotazu</span><span class="sxs-lookup"><span data-stu-id="33a30-112">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [<span data-ttu-id="33a30-113">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="33a30-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
