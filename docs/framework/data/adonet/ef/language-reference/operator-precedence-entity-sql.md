---
title: Priorita operátorů (entita SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: ab5158a2af18a422cb82f0d44412bcd85a04dc2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764015"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="24086-102">Priorita operátorů (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="24086-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="24086-103">Když [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu má více operátorů, operátorů určuje pořadí, ve kterém se provádí operace.</span><span class="sxs-lookup"><span data-stu-id="24086-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="24086-104">Pořadí zpracování může významně ovlivnit výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="24086-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="24086-105">Operátory mají přednost před úrovně, uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="24086-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="24086-106">Operátor s vyšší úrovní bude vyhodnocena před operátor s nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="24086-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="24086-107">úroveň</span><span class="sxs-lookup"><span data-stu-id="24086-107">Level</span></span>|<span data-ttu-id="24086-108">Typ operace</span><span class="sxs-lookup"><span data-stu-id="24086-108">Operation type</span></span>|<span data-ttu-id="24086-109">Operátor</span><span class="sxs-lookup"><span data-stu-id="24086-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="24086-110">1</span><span class="sxs-lookup"><span data-stu-id="24086-110">1</span></span>|<span data-ttu-id="24086-111">primární</span><span class="sxs-lookup"><span data-stu-id="24086-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="24086-112">2</span><span class="sxs-lookup"><span data-stu-id="24086-112">2</span></span>|<span data-ttu-id="24086-113">Unární</span><span class="sxs-lookup"><span data-stu-id="24086-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="24086-114">3</span><span class="sxs-lookup"><span data-stu-id="24086-114">3</span></span>|<span data-ttu-id="24086-115">Multiplikativní</span><span class="sxs-lookup"><span data-stu-id="24086-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="24086-116">4</span><span class="sxs-lookup"><span data-stu-id="24086-116">4</span></span>|<span data-ttu-id="24086-117">Doplňkové</span><span class="sxs-lookup"><span data-stu-id="24086-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="24086-118">5</span><span class="sxs-lookup"><span data-stu-id="24086-118">5</span></span>|<span data-ttu-id="24086-119">Řazení</span><span class="sxs-lookup"><span data-stu-id="24086-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="24086-120">6</span><span class="sxs-lookup"><span data-stu-id="24086-120">6</span></span>|<span data-ttu-id="24086-121">Rovnost</span><span class="sxs-lookup"><span data-stu-id="24086-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="24086-122">7</span><span class="sxs-lookup"><span data-stu-id="24086-122">7</span></span>|<span data-ttu-id="24086-123">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="24086-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="24086-124">8</span><span class="sxs-lookup"><span data-stu-id="24086-124">8</span></span>|<span data-ttu-id="24086-125">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="24086-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="24086-126">Když dva operátory ve výrazu mít stejnou úroveň operátor přednost, vlevo se vyhodnocují na pravé straně na základě pozice v dotazu.</span><span class="sxs-lookup"><span data-stu-id="24086-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="24086-127">Například `x+y-z` je vyhodnoceno jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="24086-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="24086-128">Závorky můžete použít k přepsání definovaná přednost operátorů v dotazu.</span><span class="sxs-lookup"><span data-stu-id="24086-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="24086-129">Všechna data v závorkách vyhodnotí, je nejprve yield jeden výsledek před výsledek lze všechny operátorem mimo závorkách.</span><span class="sxs-lookup"><span data-stu-id="24086-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="24086-130">Například `x+y*z` vynásobí `y` podle `z` a potom přidá `x`, ale `(x+y)*z` přidá `x` k `y` a potom vynásobí výsledek podle `z`.</span><span class="sxs-lookup"><span data-stu-id="24086-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24086-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="24086-131">See Also</span></span>  
 [<span data-ttu-id="24086-132">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="24086-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
