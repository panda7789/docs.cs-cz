---
title: Literály s hodnotou null a odvození typu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: bb2d9184e17ee2a9916a731eb20eefa105a73753
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249821"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="f8ce7-102">Literály s hodnotou null a odvození typu (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f8ce7-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="f8ce7-103">Literály null jsou kompatibilní s jakýmkoli typem v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systému typů.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="f8ce7-104">Nicméně pro typ literálu s hodnotou null, který má být odvozen správně, ukládá [!INCLUDE[esql](../../../../../../includes/esql-md.md)] určitá omezení, kde lze použít literál null.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="f8ce7-105">Typové hodnoty null</span><span class="sxs-lookup"><span data-stu-id="f8ce7-105">Typed Nulls</span></span>  
 <span data-ttu-id="f8ce7-106">Typové hodnoty null lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="f8ce7-107">Odvození typu není vyžadováno pro zadané hodnoty null, protože je znám typ.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="f8ce7-108">Například můžete vytvořit hodnotu null typu Int16 s následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcí:</span><span class="sxs-lookup"><span data-stu-id="f8ce7-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="f8ce7-109">Volné literály s nulovým číslem</span><span class="sxs-lookup"><span data-stu-id="f8ce7-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="f8ce7-110">Volné literály s hodnotou null lze použít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="f8ce7-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="f8ce7-111">Jako argument pro výraz CAST nebo považovat.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="f8ce7-112">Toto je doporučený způsob vytvoření typovaného výrazu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="f8ce7-113">Jako argument metody nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-113">As an argument to a method or a function.</span></span> <span data-ttu-id="f8ce7-114">Platí standardní pravidla přetížení.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="f8ce7-115">Jako jeden z argumentů aritmetického výrazu, jako je například +,-nebo/.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="f8ce7-116">Ostatní argumenty nemohou být literály null, jinak odvození typu není možné.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="f8ce7-117">Jako kterýkoli z argumentů logického výrazu (a, nebo).</span><span class="sxs-lookup"><span data-stu-id="f8ce7-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="f8ce7-118">Všechny argumenty jsou známy jako typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="f8ce7-119">, Protože argument má hodnotu NULL nebo není NULL výraz.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="f8ce7-120">Jako jeden nebo více argumentů výrazu LIKE.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="f8ce7-121">Očekává se, že všechny argumenty budou řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="f8ce7-122">Jako jeden nebo více argumentů konstruktoru pojmenovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="f8ce7-123">Jako jeden nebo více argumentů konstruktoru multiset.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="f8ce7-124">Nejméně jeden argument konstruktoru multiset musí být výraz, který není literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="f8ce7-125">Jako jeden nebo více výrazů THEN nebo ELSE ve výrazu CASE.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="f8ce7-126">Nejméně jeden z výrazů THEN nebo ELSE ve výrazu CASE musí být výrazem jiným než literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="f8ce7-127">V jiných scénářích nelze použít prázdné literály s nulovým číslem.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="f8ce7-128">Nelze je například použít jako argumenty konstruktoru řádku.</span><span class="sxs-lookup"><span data-stu-id="f8ce7-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ce7-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8ce7-129">See also</span></span>

- [<span data-ttu-id="f8ce7-130">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8ce7-130">Entity SQL Overview</span></span>](entity-sql-overview.md)
