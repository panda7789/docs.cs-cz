---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833895"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="0f249-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0f249-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="0f249-103">Odkazuje na referenční hodnotu a vytvoří výsledek tohoto předaného odkazu.</span><span class="sxs-lookup"><span data-stu-id="0f249-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f249-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f249-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="0f249-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f249-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0f249-106">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="0f249-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f249-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f249-107">Return Value</span></span>  
 <span data-ttu-id="0f249-108">Hodnota odkazované entity</span><span class="sxs-lookup"><span data-stu-id="0f249-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f249-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f249-109">Remarks</span></span>  
 <span data-ttu-id="0f249-110">Operátor DEREF odkazuje na referenční hodnotu a generuje výsledek tohoto odkázání.</span><span class="sxs-lookup"><span data-stu-id="0f249-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="0f249-111">Například pokud `r` je odkaz typu ref @ no__t-1T >, `Deref(r)` je výraz typu `T`, který vede k entitě, na kterou odkazuje `r`.</span><span class="sxs-lookup"><span data-stu-id="0f249-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="0f249-112">Pokud má referenční hodnota hodnotu null nebo je dangling (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0f249-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f249-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f249-113">Example</span></span>  
 <span data-ttu-id="0f249-114">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor DEREF k tomu, aby převedl odkaz na referenční hodnotu a vytvořil výsledek tohoto odkázání.</span><span class="sxs-lookup"><span data-stu-id="0f249-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="0f249-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0f249-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0f249-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0f249-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0f249-117">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0f249-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="0f249-118">Předat následující dotaz jako argument metodě ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="0f249-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="0f249-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f249-119">See also</span></span>

- [<span data-ttu-id="0f249-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0f249-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0f249-121">REF</span><span class="sxs-lookup"><span data-stu-id="0f249-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="0f249-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="0f249-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="0f249-123">KEY</span><span class="sxs-lookup"><span data-stu-id="0f249-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="0f249-124">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="0f249-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
