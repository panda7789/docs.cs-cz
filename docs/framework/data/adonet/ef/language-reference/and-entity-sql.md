---
title: '&amp;&amp;ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251318"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="c5c37-102">&amp;&amp;ANI (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c5c37-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="c5c37-103">Vrátí `true` , zda jsou `true`oba výrazy; v `false` opačném případě nebo `NULL`.</span><span class="sxs-lookup"><span data-stu-id="c5c37-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5c37-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5c37-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c5c37-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="c5c37-106">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c5c37-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c37-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5c37-107">Remarks</span></span>  
 <span data-ttu-id="c5c37-108">Dvojité ampersandy (& &) mají stejné funkce jako operátor AND.</span><span class="sxs-lookup"><span data-stu-id="c5c37-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="c5c37-109">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="c5c37-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="c5c37-110">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="c5c37-110">TRUE</span></span>|<span data-ttu-id="c5c37-111">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="c5c37-111">FALSE</span></span>|<span data-ttu-id="c5c37-112">NULL</span><span class="sxs-lookup"><span data-stu-id="c5c37-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="c5c37-113">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="c5c37-113">FALSE</span></span>|<span data-ttu-id="c5c37-114">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="c5c37-114">FALSE</span></span>|<span data-ttu-id="c5c37-115">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="c5c37-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="c5c37-116">NULL</span><span class="sxs-lookup"><span data-stu-id="c5c37-116">NULL</span></span>|<span data-ttu-id="c5c37-117">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="c5c37-117">FALSE</span></span>|<span data-ttu-id="c5c37-118">NULL</span><span class="sxs-lookup"><span data-stu-id="c5c37-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5c37-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5c37-119">Example</span></span>  
 <span data-ttu-id="c5c37-120">Následující Entity SQL dotaz ukazuje použití operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="c5c37-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="c5c37-121">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c5c37-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c5c37-122">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="c5c37-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c5c37-123">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c5c37-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c5c37-124">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="c5c37-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="c5c37-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5c37-125">See also</span></span>

- [<span data-ttu-id="c5c37-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c5c37-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
