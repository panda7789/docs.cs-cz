---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: d4293b8e027f7f0f7eabac7ad9c8a9852ddd3a80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178474"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="5b951-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b951-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="5b951-103">Vytvoří instanci multisady ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="5b951-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="5b951-104">Všechny hodnoty v konstruktor MULTISET musí být kompatibilní `T`.</span><span class="sxs-lookup"><span data-stu-id="5b951-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="5b951-105">Multiset – prázdný konstruktory nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="5b951-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b951-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b951-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b951-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b951-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5b951-108">Libovolný platný seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="5b951-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b951-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b951-109">Return Value</span></span>  
 <span data-ttu-id="5b951-110">Kolekce typu MULTIMNOŽINA\<T >.</span><span class="sxs-lookup"><span data-stu-id="5b951-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b951-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b951-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5b951-112">nabízí tři druhy konstruktory: řádek konstruktory, konstruktory objektu a konstruktory multiset (nebo kolekce).</span><span class="sxs-lookup"><span data-stu-id="5b951-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="5b951-113">Další informace najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5b951-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5b951-114">Konstruktor multiset vytvoří instanci multisady ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="5b951-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="5b951-115">Všechny hodnoty v konstruktoru musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="5b951-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="5b951-116">Například následující výraz vytvoří multiset celých čísel.</span><span class="sxs-lookup"><span data-stu-id="5b951-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="5b951-117">Multiset – vnořené literály jsou podporovány pouze při zabalení multiset má jeden prvek multiset –; například `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="5b951-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="5b951-118">Pokud multiset zabalení má více elementů multiset – (například `{{1, 2}, {3, 4}}`), vnořené multiset – literály nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="5b951-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b951-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b951-119">Example</span></span>  
 <span data-ttu-id="5b951-120">Následující dotaz Entity SQL používá operátor MULTISET k vytvoření instance multisady ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="5b951-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="5b951-121">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5b951-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5b951-122">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="5b951-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5b951-123">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5b951-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="5b951-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="5b951-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="5b951-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b951-125">See also</span></span>

- [<span data-ttu-id="5b951-126">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="5b951-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="5b951-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5b951-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
