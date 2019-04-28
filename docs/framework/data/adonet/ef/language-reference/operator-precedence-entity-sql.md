---
title: Priorita operátorů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760347"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="18169-102">Priorita operátorů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="18169-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="18169-103">Když [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz obsahuje více operátorů, určuje priorita operátorů pořadí, ve kterém jsou operace prováděny.</span><span class="sxs-lookup"><span data-stu-id="18169-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="18169-104">Pořadí provádění může významně ovlivnit výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="18169-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="18169-105">Operátory mají přednost před úrovně je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="18169-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="18169-106">Operátor s vyšší úrovní je vyhodnoceno před operátor s nižší úrovní.</span><span class="sxs-lookup"><span data-stu-id="18169-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="18169-107">úroveň</span><span class="sxs-lookup"><span data-stu-id="18169-107">Level</span></span>|<span data-ttu-id="18169-108">Typ operace</span><span class="sxs-lookup"><span data-stu-id="18169-108">Operation type</span></span>|<span data-ttu-id="18169-109">Operátor</span><span class="sxs-lookup"><span data-stu-id="18169-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="18169-110">1</span><span class="sxs-lookup"><span data-stu-id="18169-110">1</span></span>|<span data-ttu-id="18169-111">Primární</span><span class="sxs-lookup"><span data-stu-id="18169-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="18169-112">2</span><span class="sxs-lookup"><span data-stu-id="18169-112">2</span></span>|<span data-ttu-id="18169-113">Unární</span><span class="sxs-lookup"><span data-stu-id="18169-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="18169-114">3</span><span class="sxs-lookup"><span data-stu-id="18169-114">3</span></span>|<span data-ttu-id="18169-115">Násobení</span><span class="sxs-lookup"><span data-stu-id="18169-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="18169-116">4</span><span class="sxs-lookup"><span data-stu-id="18169-116">4</span></span>|<span data-ttu-id="18169-117">Additive</span><span class="sxs-lookup"><span data-stu-id="18169-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="18169-118">5</span><span class="sxs-lookup"><span data-stu-id="18169-118">5</span></span>|<span data-ttu-id="18169-119">Řazení</span><span class="sxs-lookup"><span data-stu-id="18169-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="18169-120">6</span><span class="sxs-lookup"><span data-stu-id="18169-120">6</span></span>|<span data-ttu-id="18169-121">Rovnost</span><span class="sxs-lookup"><span data-stu-id="18169-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="18169-122">7</span><span class="sxs-lookup"><span data-stu-id="18169-122">7</span></span>|<span data-ttu-id="18169-123">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="18169-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="18169-124">8</span><span class="sxs-lookup"><span data-stu-id="18169-124">8</span></span>|<span data-ttu-id="18169-125">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="18169-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="18169-126">Když dva operátory ve výrazu dosahovat stejné úrovně priority operátoru, že jsou vyhodnoceny zleva doprava, na základě jejich pozice v dotazu.</span><span class="sxs-lookup"><span data-stu-id="18169-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="18169-127">Například `x+y-z` se vyhodnotí jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="18169-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="18169-128">Můžete použít závorky k přepsání definovaná priorita operátorů v dotazu.</span><span class="sxs-lookup"><span data-stu-id="18169-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="18169-129">Všechno, co v závorkách je vyhodnocen jako první pozastavit před jeden výsledek, výsledek je možné všechny operátorem mimo závorky.</span><span class="sxs-lookup"><span data-stu-id="18169-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="18169-130">Například `x+y*z` vynásobí `y` podle `z` a pak přidá `x`, ale `(x+y)*z` přidá `x` k `y` a pak vynásobí výsledků `z`.</span><span class="sxs-lookup"><span data-stu-id="18169-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18169-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18169-131">See also</span></span>

- [<span data-ttu-id="18169-132">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="18169-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
