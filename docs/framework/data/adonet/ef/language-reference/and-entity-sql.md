---
title: '&amp;&amp;(A) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150506"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="1b896-102">&amp;&amp;(A) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="1b896-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="1b896-103">Vrátí, `true` pokud jsou `true`oba výrazy ; jinak, `false` `NULL`nebo .</span><span class="sxs-lookup"><span data-stu-id="1b896-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b896-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b896-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="1b896-105">– nebo –</span><span class="sxs-lookup"><span data-stu-id="1b896-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1b896-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1b896-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="1b896-107">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b896-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b896-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b896-108">Remarks</span></span>  
 <span data-ttu-id="1b896-109">Dvojité ampersands (&&) mají stejné funkce jako operátor AND.</span><span class="sxs-lookup"><span data-stu-id="1b896-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="1b896-110">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="1b896-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="1b896-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="1b896-111">TRUE</span></span>|<span data-ttu-id="1b896-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="1b896-112">FALSE</span></span>|<span data-ttu-id="1b896-113">NULL</span><span class="sxs-lookup"><span data-stu-id="1b896-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="1b896-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="1b896-114">FALSE</span></span>|<span data-ttu-id="1b896-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="1b896-115">FALSE</span></span>|<span data-ttu-id="1b896-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="1b896-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="1b896-117">NULL</span><span class="sxs-lookup"><span data-stu-id="1b896-117">NULL</span></span>|<span data-ttu-id="1b896-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="1b896-118">FALSE</span></span>|<span data-ttu-id="1b896-119">NULL</span><span class="sxs-lookup"><span data-stu-id="1b896-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b896-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b896-120">Example</span></span>  
 <span data-ttu-id="1b896-121">Následující dotaz ENTITY SQL ukazuje, jak používat operátor AND.</span><span class="sxs-lookup"><span data-stu-id="1b896-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="1b896-122">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="1b896-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1b896-123">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="1b896-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1b896-124">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1b896-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1b896-125">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="1b896-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="1b896-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b896-126">See also</span></span>

- [<span data-ttu-id="1b896-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1b896-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
