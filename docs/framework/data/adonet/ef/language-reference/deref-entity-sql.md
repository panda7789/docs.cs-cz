---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 1ba562ba6542e6ab0d62f1f8348434ae4f4c9b13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305179"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="3aaa5-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3aaa5-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="3aaa5-103">Přístupů přes ukazatel referenčními hodnotami a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aaa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aaa5-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="3aaa5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3aaa5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3aaa5-106">Libovolný výraz platný dotaz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aaa5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3aaa5-107">Return Value</span></span>  
 <span data-ttu-id="3aaa5-108">Hodnota entity, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aaa5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3aaa5-109">Remarks</span></span>  
 <span data-ttu-id="3aaa5-110">Operátor DEREF přístupů přes ukazatel, hodnota odkazu a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="3aaa5-111">Například pokud `r` odkaz na typ ref\<T >, `Deref(r)` je výraz typu `T` , která poskytuje entita odkazuje `r`.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="3aaa5-112">Pokud hodnota odkazu je null nebo je nepropojená (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aaa5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3aaa5-113">Example</span></span>  
 <span data-ttu-id="3aaa5-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor DEREF pokouší dereferencovat referenčními hodnotami a přístupu přes ukazatel výsledku, který vytvoří.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="3aaa5-115">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3aaa5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3aaa5-116">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="3aaa5-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3aaa5-117">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3aaa5-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="3aaa5-118">Následující dotaz předejte jako argument k metodě ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="3aaa5-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="3aaa5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aaa5-119">See also</span></span>

- [<span data-ttu-id="3aaa5-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3aaa5-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3aaa5-121">REF</span><span class="sxs-lookup"><span data-stu-id="3aaa5-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="3aaa5-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="3aaa5-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="3aaa5-123">KEY</span><span class="sxs-lookup"><span data-stu-id="3aaa5-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="3aaa5-124">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="3aaa5-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
