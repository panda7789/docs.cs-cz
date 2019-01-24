---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 4d0bed2fb000e96e9fd0ceac6ea90e19b8fa7514
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554852"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="ed1cb-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed1cb-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="ed1cb-103">Kombinuje dvě `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed1cb-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed1cb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed1cb-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="ed1cb-106">Libovolný platný výraz, který vrací `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed1cb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed1cb-107">Return Value</span></span>  
 <span data-ttu-id="ed1cb-108">`true` Pokud některá z podmínek je `true`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed1cb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed1cb-109">Remarks</span></span>  
 <span data-ttu-id="ed1cb-110">NEBO se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="ed1cb-111">Používá se ke sloučení dvě podmínky.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-111">It is used to combine two conditions.</span></span> <span data-ttu-id="ed1cb-112">Pokud více než jeden logický operátor se používá v příkazu, nebo operátory jsou vyhodnocovány po operátory.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="ed1cb-113">Pořadí vyhodnocení však můžete změnit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="ed1cb-114">Double svislé čáry (&#124;&#124;) mají stejné funkce jako operátor OR.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="ed1cb-115">Následující tabulka uvádí možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="ed1cb-116">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-116">TRUE</span></span>|<span data-ttu-id="ed1cb-117">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-117">TRUE</span></span>|<span data-ttu-id="ed1cb-118">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="ed1cb-119">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-119">TRUE</span></span>|<span data-ttu-id="ed1cb-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-120">FALSE</span></span>|<span data-ttu-id="ed1cb-121">NULL</span><span class="sxs-lookup"><span data-stu-id="ed1cb-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="ed1cb-122">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="ed1cb-122">TRUE</span></span>|<span data-ttu-id="ed1cb-123">NULL</span><span class="sxs-lookup"><span data-stu-id="ed1cb-123">NULL</span></span>|<span data-ttu-id="ed1cb-124">NULL</span><span class="sxs-lookup"><span data-stu-id="ed1cb-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed1cb-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed1cb-125">Example</span></span>  
 <span data-ttu-id="ed1cb-126">Následující dotaz Entity SQL používá operátor nebo kombinace obou `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="ed1cb-127">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ed1cb-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed1cb-128">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="ed1cb-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed1cb-129">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ed1cb-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ed1cb-130">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ed1cb-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="ed1cb-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed1cb-131">See also</span></span>
- [<span data-ttu-id="ed1cb-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ed1cb-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
