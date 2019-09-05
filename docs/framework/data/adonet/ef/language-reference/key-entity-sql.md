---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 44ab5352c3b2a94cb210c3de775d2347d2df7fe7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250487"
---
# <a name="key-entity-sql"></a><span data-ttu-id="12fe1-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="12fe1-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="12fe1-103">Extrahuje klíč odkazu nebo výrazu entity.</span><span class="sxs-lookup"><span data-stu-id="12fe1-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12fe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12fe1-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="12fe1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12fe1-105">Remarks</span></span>  
 <span data-ttu-id="12fe1-106">Klíč entity obsahuje hodnoty klíče ve správném pořadí v zadané entitě nebo odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="12fe1-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="12fe1-107">Vzhledem k tomu, že více sad entit může být založené na stejném typu, může se stejný klíč objevit v každé sadě entit.</span><span class="sxs-lookup"><span data-stu-id="12fe1-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="12fe1-108">Chcete-li získat jedinečný odkaz, `REF`použijte.</span><span class="sxs-lookup"><span data-stu-id="12fe1-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="12fe1-109">Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="12fe1-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="12fe1-110">V následujícím příkladu je operátor Key předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu.</span><span class="sxs-lookup"><span data-stu-id="12fe1-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="12fe1-111">V takovém případě typ záznamu s přesně jedním polem odpovídajícím `Id` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="12fe1-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="12fe1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="12fe1-112">Example</span></span>  
 <span data-ttu-id="12fe1-113">Následující Entity SQL dotaz pomocí operátoru KEY extrahuje klíčovou část výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="12fe1-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="12fe1-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="12fe1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="12fe1-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="12fe1-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="12fe1-116">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="12fe1-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="12fe1-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="12fe1-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="12fe1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12fe1-118">See also</span></span>

- [<span data-ttu-id="12fe1-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="12fe1-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="12fe1-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="12fe1-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="12fe1-121">REF</span><span class="sxs-lookup"><span data-stu-id="12fe1-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="12fe1-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="12fe1-122">DEREF</span></span>](deref-entity-sql.md)
