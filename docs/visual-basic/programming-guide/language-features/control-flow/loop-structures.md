---
title: Struktury smyčky
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 0a75205a7d52c332094d624d082e5db3e89447f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353918"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="2249b-102">Struktury smyčky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2249b-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="2249b-103">Struktury smyčky Visual Basic umožňují spustit jeden nebo více řádků kódu opakovaně.</span><span class="sxs-lookup"><span data-stu-id="2249b-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="2249b-104">Příkazy lze opakovat ve struktuře smyčky, dokud není podmínka `True`, dokud není podmínka `False`, zadaného počtu opakování nebo jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="2249b-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="2249b-105">Následující ilustrace znázorňuje strukturu smyčky, která spouští sadu příkazů, dokud podmínka nebude pravdivá:</span><span class="sxs-lookup"><span data-stu-id="2249b-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Vývojový diagram, který zobrazuje do... Do smyčky.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="2249b-107">Cykly ve smyčce</span><span class="sxs-lookup"><span data-stu-id="2249b-107">While Loops</span></span>  
 <span data-ttu-id="2249b-108">Konstrukce `While`...`End While` spouští sadu příkazů, dokud je `True`podmínka zadaná v příkazu `While`.</span><span class="sxs-lookup"><span data-stu-id="2249b-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="2249b-109">Další informace najdete v části [while... Příkaz End While](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2249b-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="2249b-110">Do smyček</span><span class="sxs-lookup"><span data-stu-id="2249b-110">Do Loops</span></span>  
 <span data-ttu-id="2249b-111">`Do`...`Loop` konstrukce umožňuje testovat podmínku buď na začátku, nebo na konci struktury smyčky.</span><span class="sxs-lookup"><span data-stu-id="2249b-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="2249b-112">Můžete také určit, jestli se má opakovat smyčka, zatímco podmínka zůstane `True` nebo dokud se ne`True`.</span><span class="sxs-lookup"><span data-stu-id="2249b-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="2249b-113">Další informace najdete v části [do... Příkaz LOOP](../../../../visual-basic/language-reference/statements/do-loop-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2249b-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="2249b-114">Smyčka for</span><span class="sxs-lookup"><span data-stu-id="2249b-114">For Loops</span></span>  
 <span data-ttu-id="2249b-115">Konstrukce `For`...`Next` provádí smyčku v určitém počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="2249b-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="2249b-116">K udržení přehledu opakování používá proměnnou ovládacího prvku smyčky, která se označuje také jako *čítač*.</span><span class="sxs-lookup"><span data-stu-id="2249b-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="2249b-117">Zadejte počáteční a koncové hodnoty pro tento čítač a můžete volitelně zadat hodnotu, o kterou se zvýší z jednoho opakování na další.</span><span class="sxs-lookup"><span data-stu-id="2249b-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="2249b-118">Další informace najdete v tématu [... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2249b-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="2249b-119">Pro každou smyčku</span><span class="sxs-lookup"><span data-stu-id="2249b-119">For Each Loops</span></span>  
 <span data-ttu-id="2249b-120">Konstrukce `For Each`...`Next` spouští sadu příkazů jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="2249b-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="2249b-121">Zadáte řídicí proměnnou smyčky, ale nemusíte určit počáteční nebo koncové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2249b-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="2249b-122">Další informace najdete v tématu [for each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2249b-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2249b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2249b-123">See also</span></span>

- [<span data-ttu-id="2249b-124">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="2249b-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="2249b-125">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="2249b-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="2249b-126">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="2249b-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="2249b-127">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="2249b-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
