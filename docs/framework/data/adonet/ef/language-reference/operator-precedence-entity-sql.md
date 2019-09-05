---
title: Priorita operátorů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249786"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="73ab8-102">Priorita operátorů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73ab8-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="73ab8-103">Pokud má [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz více operátorů, priorita operátorů určuje pořadí, ve kterém jsou operace prováděny.</span><span class="sxs-lookup"><span data-stu-id="73ab8-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="73ab8-104">Pořadí spuštění může významně ovlivnit výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="73ab8-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="73ab8-105">Operátory mají úrovně priority uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="73ab8-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="73ab8-106">Operátor s vyšší úrovní je vyhodnocen před operátorem nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="73ab8-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="73ab8-107">Level</span><span class="sxs-lookup"><span data-stu-id="73ab8-107">Level</span></span>|<span data-ttu-id="73ab8-108">Typ operace</span><span class="sxs-lookup"><span data-stu-id="73ab8-108">Operation type</span></span>|<span data-ttu-id="73ab8-109">Operátor</span><span class="sxs-lookup"><span data-stu-id="73ab8-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="73ab8-110">1</span><span class="sxs-lookup"><span data-stu-id="73ab8-110">1</span></span>|<span data-ttu-id="73ab8-111">Primární</span><span class="sxs-lookup"><span data-stu-id="73ab8-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="73ab8-112">2</span><span class="sxs-lookup"><span data-stu-id="73ab8-112">2</span></span>|<span data-ttu-id="73ab8-113">Unární</span><span class="sxs-lookup"><span data-stu-id="73ab8-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="73ab8-114">3</span><span class="sxs-lookup"><span data-stu-id="73ab8-114">3</span></span>|<span data-ttu-id="73ab8-115">Multiplikativní</span><span class="sxs-lookup"><span data-stu-id="73ab8-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="73ab8-116">4</span><span class="sxs-lookup"><span data-stu-id="73ab8-116">4</span></span>|<span data-ttu-id="73ab8-117">Přičítáním</span><span class="sxs-lookup"><span data-stu-id="73ab8-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="73ab8-118">5</span><span class="sxs-lookup"><span data-stu-id="73ab8-118">5</span></span>|<span data-ttu-id="73ab8-119">Řazení</span><span class="sxs-lookup"><span data-stu-id="73ab8-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="73ab8-120">6</span><span class="sxs-lookup"><span data-stu-id="73ab8-120">6</span></span>|<span data-ttu-id="73ab8-121">Rovnost</span><span class="sxs-lookup"><span data-stu-id="73ab8-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="73ab8-122">7</span><span class="sxs-lookup"><span data-stu-id="73ab8-122">7</span></span>|<span data-ttu-id="73ab8-123">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="73ab8-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="73ab8-124">8</span><span class="sxs-lookup"><span data-stu-id="73ab8-124">8</span></span>|<span data-ttu-id="73ab8-125">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="73ab8-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="73ab8-126">Pokud mají dva operátory ve výrazu stejnou úroveň priority operátora, jsou vyhodnoceny zleva doprava na základě jejich pozice v dotazu.</span><span class="sxs-lookup"><span data-stu-id="73ab8-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="73ab8-127">Například `x+y-z` je vyhodnocen jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="73ab8-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="73ab8-128">Pomocí závorek můžete přepsat definovanou prioritu operátorů v dotazu.</span><span class="sxs-lookup"><span data-stu-id="73ab8-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="73ab8-129">Vše v závorkách je nejprve vyhodnoceno a výsledkem je jeden výsledek, který může být použit libovolným operátorem mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="73ab8-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="73ab8-130">`x+y*z` Například `x` `z`vynásobí `z` apoté`x` přidá, ale `(x+y)*z` přidá do apakvynásobívýsledekhodnotou.`y` `y`</span><span class="sxs-lookup"><span data-stu-id="73ab8-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ab8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73ab8-131">See also</span></span>

- [<span data-ttu-id="73ab8-132">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="73ab8-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
