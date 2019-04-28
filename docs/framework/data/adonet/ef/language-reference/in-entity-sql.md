---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: d88f79dbfcd27f0ca0d1e26815d7d2bbee731bcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750693"
---
# <a name="in-entity-sql"></a><span data-ttu-id="48cd5-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="48cd5-102">IN (Entity SQL)</span></span>
<span data-ttu-id="48cd5-103">Určuje, zda hodnota odpovídá libovolné hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="48cd5-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48cd5-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="48cd5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="48cd5-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="48cd5-106">Libovolný platný výraz, který vrací hodnotu tak, aby odpovídaly.</span><span class="sxs-lookup"><span data-stu-id="48cd5-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="48cd5-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="48cd5-107">[ NOT ]</span></span>  
 <span data-ttu-id="48cd5-108">Určuje, že `Boolean` ve výsledku bude negovat.</span><span class="sxs-lookup"><span data-stu-id="48cd5-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="48cd5-109">Libovolný platný výraz, který vrátí kolekce, kterou chcete testovat pro shodu.</span><span class="sxs-lookup"><span data-stu-id="48cd5-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="48cd5-110">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `value`.</span><span class="sxs-lookup"><span data-stu-id="48cd5-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48cd5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48cd5-111">Return Value</span></span>  
 <span data-ttu-id="48cd5-112">`true` Pokud je hodnota nalezena v kolekci. Hodnota Null, pokud je hodnota null nebo kolekci má hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="48cd5-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="48cd5-113">Pomocí NOT IN Neguje výsledky IN.</span><span class="sxs-lookup"><span data-stu-id="48cd5-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48cd5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="48cd5-114">Example</span></span>  
 <span data-ttu-id="48cd5-115">Následující dotaz Entity SQL používá operátor k určení, zda hodnota odpovídá libovolné hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="48cd5-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="48cd5-116">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="48cd5-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="48cd5-117">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="48cd5-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="48cd5-118">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="48cd5-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="48cd5-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="48cd5-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="48cd5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48cd5-120">See also</span></span>

- [<span data-ttu-id="48cd5-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="48cd5-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
