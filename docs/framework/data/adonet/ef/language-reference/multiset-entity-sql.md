---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 8e02d2d3171c9f08333ecef7ee22e65100bdf822
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250096"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="87ee1-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="87ee1-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="87ee1-103">Vytvoří instanci multiset ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="87ee1-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="87ee1-104">Všechny hodnoty v konstruktoru MULTISET musí být kompatibilního typu `T`.</span><span class="sxs-lookup"><span data-stu-id="87ee1-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="87ee1-105">Prázdné konstruktory multiset nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="87ee1-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ee1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87ee1-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="87ee1-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="87ee1-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="87ee1-108">Libovolný platný seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="87ee1-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87ee1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87ee1-109">Return Value</span></span>  
 <span data-ttu-id="87ee1-110">Kolekce typu MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="87ee1-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ee1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87ee1-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="87ee1-112">poskytuje tři druhy konstruktorů: konstruktory řádků, konstruktory objektů a konstruktory multiset (nebo Collection).</span><span class="sxs-lookup"><span data-stu-id="87ee1-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="87ee1-113">Další informace naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="87ee1-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="87ee1-114">Konstruktor multiset vytvoří instanci multiset ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="87ee1-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="87ee1-115">Všechny hodnoty v konstruktoru musí být kompatibilního typu.</span><span class="sxs-lookup"><span data-stu-id="87ee1-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="87ee1-116">Například následující výraz vytvoří multiset celých čísel.</span><span class="sxs-lookup"><span data-stu-id="87ee1-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="87ee1-117">Vnořené literály multiset jsou podporovány pouze v případě, že multiset zalamování má jeden prvek multiset; například `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="87ee1-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="87ee1-118">Pokud má multiset zalamování více prvků multiset (například `{{1, 2}, {3, 4}}`), vnořené literály multiset nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="87ee1-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ee1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="87ee1-119">Example</span></span>  
 <span data-ttu-id="87ee1-120">Následující Entity SQL dotaz používá operátor MULTISET k vytvoření instance MULTISET ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="87ee1-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="87ee1-121">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="87ee1-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="87ee1-122">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="87ee1-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="87ee1-123">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="87ee1-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="87ee1-124">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="87ee1-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="87ee1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87ee1-125">See also</span></span>

- [<span data-ttu-id="87ee1-126">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="87ee1-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="87ee1-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="87ee1-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
