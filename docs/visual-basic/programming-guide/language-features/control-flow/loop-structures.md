---
title: Struktury smyčky (Visual Basic)
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
ms.openlocfilehash: b72eef632b4564abc69e6ebef43b940eb0950e9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523386"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="34b6e-102">Struktury smyčky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b6e-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="34b6e-103">Struktury smyčky v jazyce Visual Basic umožňují opakovaně spustit jeden nebo více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="34b6e-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="34b6e-104">Příkazy ve smyčce struktura můžete opakovat, dokud je podmínka `True`, dokud je podmínka `False`, zadaný počet opakování, nebo jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="34b6e-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="34b6e-105">Následující ilustrace znázorňuje strukturu smyčku, která spustí sadu příkazů, dokud se podmínka stane pravdivou.</span><span class="sxs-lookup"><span data-stu-id="34b6e-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="34b6e-106">![Vývojový diagram DNT... Smyčka UNTIL](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="34b6e-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="34b6e-107">Spuštění sady příkazů, dokud se podmínka stane pravdivou</span><span class="sxs-lookup"><span data-stu-id="34b6e-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="34b6e-108">Smyčky while</span><span class="sxs-lookup"><span data-stu-id="34b6e-108">While Loops</span></span>  
 <span data-ttu-id="34b6e-109">`While`... `End While` konstrukce spustí sadu příkazů tak dlouho, dokud podmínka podle `While` příkaz je `True`.</span><span class="sxs-lookup"><span data-stu-id="34b6e-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="34b6e-110">Další informace najdete v tématu [během... End While – příkaz](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34b6e-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="34b6e-111">Do Loops</span><span class="sxs-lookup"><span data-stu-id="34b6e-111">Do Loops</span></span>  
 <span data-ttu-id="34b6e-112">`Do`... `Loop` konstrukce využijete k otestování podmínky na začátku nebo konci struktury smyčky.</span><span class="sxs-lookup"><span data-stu-id="34b6e-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="34b6e-113">Můžete také určit, jestli se má opakování cyklu, zatímco zůstane podmínka `True` nebo dokud nebude `True`.</span><span class="sxs-lookup"><span data-stu-id="34b6e-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="34b6e-114">Další informace najdete v tématu [udělat... Smyčky příkaz](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34b6e-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="34b6e-115">Smyčky for</span><span class="sxs-lookup"><span data-stu-id="34b6e-115">For Loops</span></span>  
 <span data-ttu-id="34b6e-116">`For`... `Next` konstrukce provádí smyčky do sady počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="34b6e-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="34b6e-117">Použije řídicí proměnná smyčky for, zkratka *čítač*, můžete sledovat opakování.</span><span class="sxs-lookup"><span data-stu-id="34b6e-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="34b6e-118">Zadejte počáteční a koncové hodnoty tohoto čítače, a volitelně můžete zadat dobu, podle kterého jeho hodnota se zvyšuje z jednoho opakování na další.</span><span class="sxs-lookup"><span data-stu-id="34b6e-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="34b6e-119">Další informace najdete v tématu [pro... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34b6e-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="34b6e-120">Smyčky For Each</span><span class="sxs-lookup"><span data-stu-id="34b6e-120">For Each Loops</span></span>  
 <span data-ttu-id="34b6e-121">`For Each`... `Next` konstrukce spustí sadu příkazů jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="34b6e-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="34b6e-122">Zadat řídicí proměnná smyčky for, ale nemáte k určení počáteční nebo koncovou hodnotou pro něj.</span><span class="sxs-lookup"><span data-stu-id="34b6e-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="34b6e-123">Další informace najdete v tématu [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34b6e-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b6e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34b6e-124">See also</span></span>
- [<span data-ttu-id="34b6e-125">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="34b6e-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="34b6e-126">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="34b6e-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="34b6e-127">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="34b6e-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="34b6e-128">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="34b6e-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
