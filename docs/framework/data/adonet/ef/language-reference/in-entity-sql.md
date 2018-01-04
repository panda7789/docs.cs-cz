---
title: V (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 00d5a309a68ad7c1c5f363d6df3cca7a0e90ce81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="in-entity-sql"></a><span data-ttu-id="ca1d2-102">V (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ca1d2-102">IN (Entity SQL)</span></span>
<span data-ttu-id="ca1d2-103">Určuje, zda hodnota odpovídá libovolná hodnota v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca1d2-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca1d2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca1d2-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="ca1d2-106">Libovolný platný výraz, který vrací hodnotu tak, aby odpovídaly.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="ca1d2-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="ca1d2-107">[ NOT ]</span></span>  
 <span data-ttu-id="ca1d2-108">Určuje, že `Boolean` být Negované výsledek IN.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="ca1d2-109">Jakýkoli platný výraz, který vrátí kolekce k testování shody.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="ca1d2-110">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `value`.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca1d2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ca1d2-111">Return Value</span></span>  
 <span data-ttu-id="ca1d2-112">`true`Pokud je hodnota nalezena v kolekci. Hodnota Null, pokud hodnota je null nebo kolekce hodnotu null. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="ca1d2-113">Pomocí NOT IN Neguje výsledky IN.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca1d2-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca1d2-114">Example</span></span>  
 <span data-ttu-id="ca1d2-115">Následující dotaz Entity SQL používá operátor k určení, zda hodnota odpovídá libovolná hodnota v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="ca1d2-116">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ca1d2-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ca1d2-117">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ca1d2-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ca1d2-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ca1d2-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ca1d2-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="ca1d2-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="ca1d2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca1d2-120">See Also</span></span>  
 [<span data-ttu-id="ca1d2-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ca1d2-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
