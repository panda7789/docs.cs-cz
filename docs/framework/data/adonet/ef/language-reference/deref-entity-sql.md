---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251082"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="34527-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="34527-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="34527-103">Odkazuje na referenční hodnotu a vytvoří výsledek tohoto předaného odkazu.</span><span class="sxs-lookup"><span data-stu-id="34527-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34527-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34527-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="34527-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="34527-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="34527-106">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="34527-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34527-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="34527-107">Return Value</span></span>  
 <span data-ttu-id="34527-108">Hodnota odkazované entity</span><span class="sxs-lookup"><span data-stu-id="34527-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34527-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34527-109">Remarks</span></span>  
 <span data-ttu-id="34527-110">Operátor DEREF odkazuje na referenční hodnotu a generuje výsledek tohoto odkázání.</span><span class="sxs-lookup"><span data-stu-id="34527-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="34527-111">Například `r` Pokud je odkaz typu ref\<T >, `Deref(r)` je výraz typu `T` , který má za důsledek entitu, na kterou odkazuje `r`.</span><span class="sxs-lookup"><span data-stu-id="34527-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="34527-112">Pokud má referenční hodnota hodnotu null nebo je dangling (to znamená, že cíl odkazu neexistuje), výsledek operátoru DEREF má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="34527-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34527-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="34527-113">Example</span></span>  
 <span data-ttu-id="34527-114">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz pomocí operátoru DEREF odkazuje na referenční hodnotu a vytvoří výsledek tohoto zpětného odkazu.</span><span class="sxs-lookup"><span data-stu-id="34527-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="34527-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="34527-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="34527-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="34527-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="34527-117">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="34527-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="34527-118">Předat následující dotaz jako argument metodě ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="34527-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="34527-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34527-119">See also</span></span>

- [<span data-ttu-id="34527-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="34527-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="34527-121">REF</span><span class="sxs-lookup"><span data-stu-id="34527-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="34527-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="34527-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="34527-123">KEY</span><span class="sxs-lookup"><span data-stu-id="34527-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="34527-124">Strukturované typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="34527-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
