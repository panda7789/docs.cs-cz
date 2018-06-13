---
title: Null literály a odvození typu (entita SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 74ff2b459488f896c5ea6af4f7d1e045da5a7983
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764213"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="4b5b5-102">Null literály a odvození typu (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="4b5b5-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="4b5b5-103">Null – literály jsou kompatibilní s žádným typem v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] systém typů.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="4b5b5-104">Pro typ literál null na odvodit správně, ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ukládá určitá omezení, na kterém můžou použít literálu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="4b5b5-105">Hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="4b5b5-105">Typed Nulls</span></span>  
 <span data-ttu-id="4b5b5-106">Hodnotou Null lze použít kdekoli.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="4b5b5-107">Odvození typu není vyžadována pro hodnotou Null, protože typ je znám.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="4b5b5-108">Například můžete vytvořit hodnotu null typu Int16 s následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vytvořit:</span><span class="sxs-lookup"><span data-stu-id="4b5b5-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="4b5b5-109">Plovoucí Null literály</span><span class="sxs-lookup"><span data-stu-id="4b5b5-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="4b5b5-110">Plovoucí literály null lze použít v kontextech následující:</span><span class="sxs-lookup"><span data-stu-id="4b5b5-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="4b5b5-111">Jako argument k PŘETYPOVÁNÍ nebo ZPRACOVÁVAT výraz.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="4b5b5-112">Toto je doporučeným způsobem, jak vytvořit výraz typu hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="4b5b5-113">Jako argument pro metodu nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-113">As an argument to a method or a function.</span></span> <span data-ttu-id="4b5b5-114">Standardní přetížení pravidla použít.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="4b5b5-115">Jako jeden z argumentů pro aritmetické výraz například +, -, nebo /.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="4b5b5-116">Další argumenty nemůže být null literály, jinak odvození typu není možné.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="4b5b5-117">Jako některý z argumentů logický výraz (AND, OR, nebo ne).</span><span class="sxs-lookup"><span data-stu-id="4b5b5-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="4b5b5-118">Všechny argumenty jsou známé být typu logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="4b5b5-119">Jako argument výraz IS NOT NULL nebo je NULL.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="4b5b5-120">Jako jeden nebo více argumenty, které se výraz LIKE.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="4b5b5-121">Všechny argumenty jsou očekávány řetězce.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="4b5b5-122">Jako jeden nebo více argumenty pro konstruktor s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="4b5b5-123">Jako jeden nebo více argumentů multiset konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="4b5b5-124">Výraz, který není null literál musí být alespoň jeden argument multiset konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="4b5b5-125">Jako jeden nebo více výrazů ve výrazu případu pak, jinak.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="4b5b5-126">Alespoň jeden z výrazů v případu výraz pak, jinak musí být výrazem jiným než literálu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="4b5b5-127">Plovoucí literály null nelze použít v jiné scénáře.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="4b5b5-128">Například se nelze použít jako argumenty pro konstruktor row.</span><span class="sxs-lookup"><span data-stu-id="4b5b5-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5b5-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b5b5-129">See Also</span></span>  
 [<span data-ttu-id="4b5b5-130">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b5b5-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
