---
title: '&amp;&amp; (a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039954"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="db96d-102">&amp;&amp; (a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db96d-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="db96d-103">Vrátí `true`, pokud jsou oba výrazy `true`; v opačném případě `false` nebo `NULL`.</span><span class="sxs-lookup"><span data-stu-id="db96d-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db96d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db96d-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```
 
<span data-ttu-id="db96d-105">or</span><span class="sxs-lookup"><span data-stu-id="db96d-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="db96d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="db96d-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="db96d-107">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="db96d-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db96d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db96d-108">Remarks</span></span>  
 <span data-ttu-id="db96d-109">Dvojité ampersandy (& &) mají stejné funkce jako operátor AND.</span><span class="sxs-lookup"><span data-stu-id="db96d-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="db96d-110">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="db96d-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="db96d-111">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db96d-111">TRUE</span></span>|<span data-ttu-id="db96d-112">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db96d-112">FALSE</span></span>|<span data-ttu-id="db96d-113">NULL</span><span class="sxs-lookup"><span data-stu-id="db96d-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="db96d-114">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db96d-114">FALSE</span></span>|<span data-ttu-id="db96d-115">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db96d-115">FALSE</span></span>|<span data-ttu-id="db96d-116">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db96d-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="db96d-117">NULL</span><span class="sxs-lookup"><span data-stu-id="db96d-117">NULL</span></span>|<span data-ttu-id="db96d-118">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db96d-118">FALSE</span></span>|<span data-ttu-id="db96d-119">NULL</span><span class="sxs-lookup"><span data-stu-id="db96d-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db96d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="db96d-120">Example</span></span>  
 <span data-ttu-id="db96d-121">Následující Entity SQL dotaz ukazuje použití operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="db96d-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="db96d-122">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="db96d-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="db96d-123">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="db96d-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="db96d-124">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="db96d-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="db96d-125">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="db96d-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="db96d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db96d-126">See also</span></span>

- [<span data-ttu-id="db96d-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="db96d-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
