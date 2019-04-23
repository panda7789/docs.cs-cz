---
title: '&amp;&amp; (AND) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eab05f7454f8ebc88ed29030503bfa96d0c70756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308429"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="943e9-102">&amp;&amp; (AND) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="943e9-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="943e9-103">Vrátí `true` Pokud jsou oba výrazy `true`; v opačném případě `false` nebo `NULL`.</span><span class="sxs-lookup"><span data-stu-id="943e9-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="943e9-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="943e9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="943e9-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="943e9-106">Libovolný platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="943e9-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="943e9-107">Remarks</span></span>  
 <span data-ttu-id="943e9-108">Dvojité ampersandy (& &) mají stejné funkce jako operátor AND.</span><span class="sxs-lookup"><span data-stu-id="943e9-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="943e9-109">Následující tabulka uvádí možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="943e9-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="943e9-110">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="943e9-110">TRUE</span></span>|<span data-ttu-id="943e9-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="943e9-111">FALSE</span></span>|<span data-ttu-id="943e9-112">NULL</span><span class="sxs-lookup"><span data-stu-id="943e9-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="943e9-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="943e9-113">FALSE</span></span>|<span data-ttu-id="943e9-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="943e9-114">FALSE</span></span>|<span data-ttu-id="943e9-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="943e9-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="943e9-116">NULL</span><span class="sxs-lookup"><span data-stu-id="943e9-116">NULL</span></span>|<span data-ttu-id="943e9-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="943e9-117">FALSE</span></span>|<span data-ttu-id="943e9-118">NULL</span><span class="sxs-lookup"><span data-stu-id="943e9-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="943e9-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="943e9-119">Example</span></span>  
 <span data-ttu-id="943e9-120">Následující dotaz Entity SQL ukazuje, jak použít operátor AND.</span><span class="sxs-lookup"><span data-stu-id="943e9-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="943e9-121">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="943e9-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="943e9-122">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="943e9-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="943e9-123">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="943e9-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="943e9-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="943e9-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="943e9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="943e9-125">See also</span></span>

- [<span data-ttu-id="943e9-126">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="943e9-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
