---
title: KEY (Entita SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150166"
---
# <a name="key-entity-sql"></a><span data-ttu-id="8113f-102">KEY (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8113f-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="8113f-103">Extrahuje klíč odkazu nebo výrazu entity.</span><span class="sxs-lookup"><span data-stu-id="8113f-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8113f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8113f-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="8113f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8113f-105">Remarks</span></span>  
 <span data-ttu-id="8113f-106">Klíč entity obsahuje hodnoty klíče ve správném pořadí zadaného odkazu entity nebo entity.</span><span class="sxs-lookup"><span data-stu-id="8113f-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="8113f-107">Vzhledem k tomu, že více sad entit může být založeno na stejném typu, může se v každé sadě entit objevit stejný klíč.</span><span class="sxs-lookup"><span data-stu-id="8113f-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="8113f-108">Chcete-li získat jedinečný `REF`odkaz, použijte .</span><span class="sxs-lookup"><span data-stu-id="8113f-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="8113f-109">Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8113f-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="8113f-110">V následujícím příkladu je operátor klíče předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu.</span><span class="sxs-lookup"><span data-stu-id="8113f-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="8113f-111">V tomto případě typ záznamu s přesně `Id` jedním polem odpovídajícím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8113f-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="8113f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8113f-112">Example</span></span>  
 <span data-ttu-id="8113f-113">Následující dotaz entity SQL používá operátor KEY k extrahování klíčové části výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="8113f-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="8113f-114">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="8113f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8113f-115">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="8113f-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8113f-116">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8113f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8113f-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="8113f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="8113f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8113f-118">See also</span></span>

- [<span data-ttu-id="8113f-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8113f-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8113f-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8113f-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="8113f-121">Ref</span><span class="sxs-lookup"><span data-stu-id="8113f-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="8113f-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="8113f-122">DEREF</span></span>](deref-entity-sql.md)
