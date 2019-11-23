---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319587"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="1e538-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e538-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="1e538-103">Vytvoří instanci multiset ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e538-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="1e538-104">Všechny hodnoty v konstruktoru MULTISET musí být kompatibilního typu `T`.</span><span class="sxs-lookup"><span data-stu-id="1e538-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="1e538-105">Prázdné konstruktory multiset nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="1e538-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e538-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e538-106">Syntax</span></span>  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e538-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1e538-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1e538-108">Libovolný platný seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e538-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e538-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1e538-109">Return Value</span></span>  
 <span data-ttu-id="1e538-110">Kolekce typu MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="1e538-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e538-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e538-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1e538-112">poskytuje tři druhy konstruktorů: konstruktory řádků, konstruktory objektů a konstruktory multiset (nebo Collection).</span><span class="sxs-lookup"><span data-stu-id="1e538-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="1e538-113">Další informace naleznete v tématu [sestavování typů](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1e538-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="1e538-114">Konstruktor multiset vytvoří instanci multiset ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e538-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="1e538-115">Všechny hodnoty v konstruktoru musí být kompatibilního typu.</span><span class="sxs-lookup"><span data-stu-id="1e538-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="1e538-116">Například následující výraz vytvoří multiset celých čísel.</span><span class="sxs-lookup"><span data-stu-id="1e538-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="1e538-117">Vnořené literály multiset jsou podporovány pouze v případě, že multiset zalamování má jeden prvek multiset; například `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="1e538-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="1e538-118">Pokud má multiset zalamování více prvků multiset (například `{{1, 2}, {3, 4}}`), vnořené literály multiset nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="1e538-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e538-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e538-119">Example</span></span>  
 <span data-ttu-id="1e538-120">Následující Entity SQL dotaz používá operátor MULTISET k vytvoření instance MULTISET ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e538-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="1e538-121">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1e538-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1e538-122">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="1e538-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1e538-123">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1e538-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1e538-124">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1e538-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="1e538-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e538-125">See also</span></span>

- [<span data-ttu-id="1e538-126">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="1e538-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="1e538-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1e538-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
