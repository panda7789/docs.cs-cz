---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319704"
---
# <a name="key-entity-sql"></a><span data-ttu-id="be233-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="be233-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="be233-103">Extrahuje klíč odkazu nebo výrazu entity.</span><span class="sxs-lookup"><span data-stu-id="be233-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be233-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be233-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="be233-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be233-105">Remarks</span></span>  
 <span data-ttu-id="be233-106">Klíč entity obsahuje hodnoty klíče ve správném pořadí v zadané entitě nebo odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="be233-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="be233-107">Vzhledem k tomu, že více sad entit může být založené na stejném typu, může se stejný klíč objevit v každé sadě entit.</span><span class="sxs-lookup"><span data-stu-id="be233-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="be233-108">Chcete-li získat jedinečný odkaz, použijte `REF`.</span><span class="sxs-lookup"><span data-stu-id="be233-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="be233-109">Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="be233-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="be233-110">V následujícím příkladu je operátor Key předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu.</span><span class="sxs-lookup"><span data-stu-id="be233-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="be233-111">V takovém případě typ záznamu s přesně jedním polem, který odpovídá vlastnosti `Id`.</span><span class="sxs-lookup"><span data-stu-id="be233-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="be233-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="be233-112">Example</span></span>  
 <span data-ttu-id="be233-113">Následující Entity SQL dotaz pomocí operátoru KEY extrahuje klíčovou část výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="be233-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="be233-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="be233-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="be233-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="be233-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="be233-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="be233-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="be233-117">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="be233-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="be233-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be233-118">See also</span></span>

- [<span data-ttu-id="be233-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be233-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="be233-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="be233-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="be233-121">REF</span><span class="sxs-lookup"><span data-stu-id="be233-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="be233-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="be233-122">DEREF</span></span>](deref-entity-sql.md)
