---
title: KLÍČ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 820d357baf8f3e17a10ced84babc6745512e572b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230028"
---
# <a name="key-entity-sql"></a><span data-ttu-id="36d05-102">KLÍČ (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="36d05-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="36d05-103">Extrahuje klíč odkazu nebo výrazu entity.</span><span class="sxs-lookup"><span data-stu-id="36d05-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36d05-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="36d05-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36d05-105">Remarks</span></span>  
 <span data-ttu-id="36d05-106">Klíč entity obsahuje hodnoty klíče ve správném pořadí zadané entity nebo odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="36d05-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="36d05-107">Protože více sad entit může být založen na stejný typ, stejný klíč se může zobrazit v každé sadě entit.</span><span class="sxs-lookup"><span data-stu-id="36d05-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="36d05-108">Chcete-li získat jedinečný odkaz, použijte `REF`.</span><span class="sxs-lookup"><span data-stu-id="36d05-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="36d05-109">Návratový typ operátoru klíč je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="36d05-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="36d05-110">V následujícím příkladu operátor klíčů je předán odkaz na entitu BadOrder a vrátí část klíče tohoto odkazu.</span><span class="sxs-lookup"><span data-stu-id="36d05-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="36d05-111">V takovém případě se přesně jeden pole odpovídající typ záznamu `Id` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="36d05-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="36d05-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="36d05-112">Example</span></span>  
 <span data-ttu-id="36d05-113">Následující dotaz Entity SQL používá operátor klíče k extrakci část výraz s odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="36d05-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="36d05-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="36d05-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="36d05-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="36d05-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="36d05-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="36d05-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="36d05-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="36d05-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="36d05-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36d05-118">See also</span></span>

- [<span data-ttu-id="36d05-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="36d05-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="36d05-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="36d05-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="36d05-121">REF</span><span class="sxs-lookup"><span data-stu-id="36d05-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="36d05-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="36d05-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
