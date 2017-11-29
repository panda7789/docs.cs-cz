---
title: "Priorita operátorů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="35f18-102">Priorita operátorů (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="35f18-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="35f18-103">Když [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu má více operátorů, operátorů určuje pořadí, ve kterém se provádí operace.</span><span class="sxs-lookup"><span data-stu-id="35f18-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="35f18-104">Pořadí zpracování může významně ovlivnit výsledek dotazu.</span><span class="sxs-lookup"><span data-stu-id="35f18-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="35f18-105">Operátory mají přednost před úrovně, uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="35f18-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="35f18-106">Operátor s vyšší úrovní bude vyhodnocena před operátor s nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="35f18-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="35f18-107">úroveň</span><span class="sxs-lookup"><span data-stu-id="35f18-107">Level</span></span>|<span data-ttu-id="35f18-108">Typ operace</span><span class="sxs-lookup"><span data-stu-id="35f18-108">Operation type</span></span>|<span data-ttu-id="35f18-109">Operátor</span><span class="sxs-lookup"><span data-stu-id="35f18-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="35f18-110">1</span><span class="sxs-lookup"><span data-stu-id="35f18-110">1</span></span>|<span data-ttu-id="35f18-111">primární</span><span class="sxs-lookup"><span data-stu-id="35f18-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="35f18-112">2</span><span class="sxs-lookup"><span data-stu-id="35f18-112">2</span></span>|<span data-ttu-id="35f18-113">Unární</span><span class="sxs-lookup"><span data-stu-id="35f18-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="35f18-114">3</span><span class="sxs-lookup"><span data-stu-id="35f18-114">3</span></span>|<span data-ttu-id="35f18-115">Multiplikativní</span><span class="sxs-lookup"><span data-stu-id="35f18-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="35f18-116">4</span><span class="sxs-lookup"><span data-stu-id="35f18-116">4</span></span>|<span data-ttu-id="35f18-117">Doplňkové</span><span class="sxs-lookup"><span data-stu-id="35f18-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="35f18-118">5</span><span class="sxs-lookup"><span data-stu-id="35f18-118">5</span></span>|<span data-ttu-id="35f18-119">Řazení</span><span class="sxs-lookup"><span data-stu-id="35f18-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="35f18-120">6</span><span class="sxs-lookup"><span data-stu-id="35f18-120">6</span></span>|<span data-ttu-id="35f18-121">Rovnost</span><span class="sxs-lookup"><span data-stu-id="35f18-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="35f18-122">7</span><span class="sxs-lookup"><span data-stu-id="35f18-122">7</span></span>|<span data-ttu-id="35f18-123">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="35f18-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="35f18-124">8</span><span class="sxs-lookup"><span data-stu-id="35f18-124">8</span></span>|<span data-ttu-id="35f18-125">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="35f18-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="35f18-126">Když dva operátory ve výrazu mít stejnou úroveň operátor přednost, vlevo se vyhodnocují na pravé straně na základě pozice v dotazu.</span><span class="sxs-lookup"><span data-stu-id="35f18-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="35f18-127">Například `x+y-z` je vyhodnoceno jako `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="35f18-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="35f18-128">Závorky můžete použít k přepsání definovaná přednost operátorů v dotazu.</span><span class="sxs-lookup"><span data-stu-id="35f18-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="35f18-129">Všechna data v závorkách vyhodnotí, je nejprve yield jeden výsledek před výsledek lze všechny operátorem mimo závorkách.</span><span class="sxs-lookup"><span data-stu-id="35f18-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="35f18-130">Například `x+y*z` vynásobí `y` podle `z` a potom přidá `x`, ale `(x+y)*z` přidá `x` k `y` a potom vynásobí výsledek podle `z`.</span><span class="sxs-lookup"><span data-stu-id="35f18-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f18-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="35f18-131">See Also</span></span>  
 [<span data-ttu-id="35f18-132">Přehled SQL entity</span><span class="sxs-lookup"><span data-stu-id="35f18-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
