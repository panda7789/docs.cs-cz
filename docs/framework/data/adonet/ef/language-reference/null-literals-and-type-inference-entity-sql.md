---
title: Literály s hodnotou Null a odvození typu proměnné (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 3fea03146549f3d42bf08bbd5e7ce355d25bd4eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641816"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="8cea3-102">Literály s hodnotou Null a odvození typu proměnné (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8cea3-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="8cea3-103">Literály s hodnotou Null, musí být kompatibilní s žádným typem v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systém typů.</span><span class="sxs-lookup"><span data-stu-id="8cea3-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="8cea3-104">Typu literál s hodnotou null odvození správně, ale pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] má určitá omezení pro použití literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8cea3-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="8cea3-105">Zadané hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="8cea3-105">Typed Nulls</span></span>  
 <span data-ttu-id="8cea3-106">Zadané hodnoty Null lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="8cea3-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="8cea3-107">Odvození typu proměnné není požadované pro zadané hodnoty Null, protože typ je znám.</span><span class="sxs-lookup"><span data-stu-id="8cea3-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="8cea3-108">Například můžete vytvořit s hodnotou null typu Int16 následujícím [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvořit:</span><span class="sxs-lookup"><span data-stu-id="8cea3-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="8cea3-109">Plovoucí literály s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8cea3-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="8cea3-110">Plovoucí literály s hodnotou null lze použít v následujících kontextů:</span><span class="sxs-lookup"><span data-stu-id="8cea3-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="8cea3-111">Jako argument výraz PŘETYPOVÁNÍ nebo POVAŽOVAT.</span><span class="sxs-lookup"><span data-stu-id="8cea3-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="8cea3-112">Toto je doporučený postup pro vytvoření zadaný nulový výraz.</span><span class="sxs-lookup"><span data-stu-id="8cea3-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="8cea3-113">Jako argument metody nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="8cea3-113">As an argument to a method or a function.</span></span> <span data-ttu-id="8cea3-114">Platí standardní přetížení pravidla.</span><span class="sxs-lookup"><span data-stu-id="8cea3-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="8cea3-115">Jako jeden z argumentů pro aritmetický výraz jako +, -, nebo /.</span><span class="sxs-lookup"><span data-stu-id="8cea3-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="8cea3-116">Další argumenty nemůžou být literály s hodnotou null, jinak odvození typu proměnné není možné.</span><span class="sxs-lookup"><span data-stu-id="8cea3-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="8cea3-117">Jako některý z argumentů na logický výraz (AND, OR, nebo ne).</span><span class="sxs-lookup"><span data-stu-id="8cea3-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="8cea3-118">Všechny argumenty jsou známé jako typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="8cea3-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="8cea3-119">Jako argument výraz IS NULL a IS NOT NULL.</span><span class="sxs-lookup"><span data-stu-id="8cea3-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="8cea3-120">Jako jeden nebo více argumentů STEJNÉHO výrazu.</span><span class="sxs-lookup"><span data-stu-id="8cea3-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="8cea3-121">Všechny argumenty jsou má být řetězce.</span><span class="sxs-lookup"><span data-stu-id="8cea3-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="8cea3-122">Jako jeden nebo více argumentů konstruktoru s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="8cea3-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="8cea3-123">Jako jeden nebo více argumentů pro konstruktor multiset.</span><span class="sxs-lookup"><span data-stu-id="8cea3-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="8cea3-124">Alespoň jeden argument pro konstruktor multiset musí být výraz, který není literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8cea3-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="8cea3-125">Jako jeden nebo více výrazů ve výrazu případu potom nebo jinak.</span><span class="sxs-lookup"><span data-stu-id="8cea3-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="8cea3-126">Nejméně jeden z výrazů v výraz CASE pak nebo jinak musí být výrazem jiným než literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8cea3-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="8cea3-127">Plovoucí literály s hodnotou null nelze použít v jiných scénářích.</span><span class="sxs-lookup"><span data-stu-id="8cea3-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="8cea3-128">Například nelze je použít jako argumenty pro konstruktor row.</span><span class="sxs-lookup"><span data-stu-id="8cea3-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cea3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cea3-129">See also</span></span>

- [<span data-ttu-id="8cea3-130">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8cea3-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
