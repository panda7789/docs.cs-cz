---
title: 'Postupy: spuštění Polymorfního dotazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: ae491d0eeda7f8703dca174bdf4c5c847f78e675
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489692"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="21955-102">Postupy: spuštění Polymorfního dotazu</span><span class="sxs-lookup"><span data-stu-id="21955-102">How to: Execute a Polymorphic Query</span></span>
<span data-ttu-id="21955-103">Toto téma ukazuje, jak spustit polymorfní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazování pomocí [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="21955-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="21955-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="21955-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="21955-105">Přidat [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) do vašeho projektu a konfigurace projektu pro použití rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="21955-105">Add the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="21955-106">Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="21955-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="21955-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="21955-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="21955-108">Upravit konceptuálního modelu má tabulka za hierrachy dědičnosti pomocí následujících kroků v [návod: mapování dědičnosti - Table za Hierarchy](https://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).</span><span class="sxs-lookup"><span data-stu-id="21955-108">Modify the conceptual model to have a table-per-hierrachy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21955-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="21955-109">Example</span></span>  
 <span data-ttu-id="21955-110">Následující příklad používá operátor OFTYPE k získání a zobrazení kolekce pouze `OnsiteCourses` z kolekce `Courses`.</span><span class="sxs-lookup"><span data-stu-id="21955-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a><span data-ttu-id="21955-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="21955-111">See Also</span></span>  
 [<span data-ttu-id="21955-112">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="21955-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="21955-113">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="21955-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
