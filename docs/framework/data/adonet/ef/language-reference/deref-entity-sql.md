---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: abe47f8c72abe13bd5c27fe10a412ff94ab861cf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384964"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="b3420-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b3420-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="b3420-103">Přístupů přes ukazatel referenčními hodnotami a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b3420-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3420-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3420-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3420-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3420-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b3420-106">Libovolný výraz platný dotaz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="b3420-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3420-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b3420-107">Return Value</span></span>  
 <span data-ttu-id="b3420-108">Hodnota entity, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="b3420-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3420-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3420-109">Remarks</span></span>  
 <span data-ttu-id="b3420-110">Operátor DEREF přístupů přes ukazatel, hodnota odkazu a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="b3420-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="b3420-111">Například pokud `r` odkaz na typ ref\<T >, `Deref(r)` je výraz typu `T` , která poskytuje entita odkazuje `r`.</span><span class="sxs-lookup"><span data-stu-id="b3420-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="b3420-112">Pokud hodnota odkazu je null nebo je nepropojená (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b3420-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3420-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3420-113">Example</span></span>  
 <span data-ttu-id="b3420-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor DEREF pokouší dereferencovat referenčními hodnotami a přístupu přes ukazatel výsledku, který vytvoří.</span><span class="sxs-lookup"><span data-stu-id="b3420-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="b3420-115">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b3420-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b3420-116">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="b3420-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b3420-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b3420-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="b3420-118">Následující dotaz předejte jako argument k metodě ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="b3420-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="b3420-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3420-119">See Also</span></span>  
 [<span data-ttu-id="b3420-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b3420-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b3420-121">REF</span><span class="sxs-lookup"><span data-stu-id="b3420-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="b3420-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="b3420-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="b3420-123">KEY</span><span class="sxs-lookup"><span data-stu-id="b3420-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="b3420-124">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="b3420-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
