---
title: MULTIMNOŽINA (entita SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: df194a26b36ba50d7b55c3dda6053c883ba9b228
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="0511d-102">MULTIMNOŽINA (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0511d-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="0511d-103">Vytvoří instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="0511d-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="0511d-104">Všechny hodnoty ve MULTISET konstruktor musí být kompatibilní typu `T`.</span><span class="sxs-lookup"><span data-stu-id="0511d-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="0511d-105">Prázdný multiset konstruktory nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0511d-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0511d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0511d-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="0511d-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="0511d-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0511d-108">Žádný platný seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="0511d-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0511d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0511d-109">Return Value</span></span>  
 <span data-ttu-id="0511d-110">Kolekci typu MULTIMNOŽINA\<T >.</span><span class="sxs-lookup"><span data-stu-id="0511d-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0511d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0511d-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0511d-112"> poskytuje tři druhy konstruktory: řádek konstruktory, objekt konstruktorů a konstruktorů multiset (nebo kolekce).</span><span class="sxs-lookup"><span data-stu-id="0511d-112"> provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="0511d-113">Další informace najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0511d-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="0511d-114">Multimnožinové konstruktoru vytvoří instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="0511d-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="0511d-115">Všechny hodnoty v konstruktoru musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="0511d-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="0511d-116">Například následující výraz vytvoří multimnožina celých čísel.</span><span class="sxs-lookup"><span data-stu-id="0511d-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="0511d-117">Vnořené multiset literály jsou podporována pouze v případě mutiset zabalení má jeden prvek multiset; například `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="0511d-117">Nested multiset literals are only supported when a wrapping mutiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="0511d-118">Když multimnožina zabalení má více elementů multiset (například `{{1, 2}, {3, 4}}`), nejsou podporovány literály vnořené multiset.</span><span class="sxs-lookup"><span data-stu-id="0511d-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0511d-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="0511d-119">Example</span></span>  
 <span data-ttu-id="0511d-120">Následující dotaz Entity SQL pomocí operátoru MULTIMNOŽINA vytvořit instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="0511d-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="0511d-121">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0511d-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0511d-122">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0511d-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0511d-123">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0511d-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0511d-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="0511d-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="0511d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="0511d-125">See Also</span></span>  
 [<span data-ttu-id="0511d-126">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="0511d-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="0511d-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0511d-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
