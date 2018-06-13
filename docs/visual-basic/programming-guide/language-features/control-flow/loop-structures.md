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
ms.openlocfilehash: 8138609f06d82b53ef5b5afb480e8609461ffc33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647888"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="b316c-102">Struktury smyčky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b316c-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="b316c-103">Struktury smyčky jazyka Visual Basic umožňují opakovaně spustit jeden nebo více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="b316c-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="b316c-104">Příkazy v struktury smyčky můžete opakujte, dokud nebude podmínku `True`, dokud nebude podmínku `False`, zadat počet opakování, nebo jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="b316c-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="b316c-105">Následující obrázek znázorňuje smyčky strukturu, která spustí sadu příkazů, dokud se stav změní na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="b316c-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="b316c-106">![Vývojový diagram DNT... Dokud smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="b316c-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="b316c-107">Spuštění sadu příkazů, dokud se stav změní na hodnotu true</span><span class="sxs-lookup"><span data-stu-id="b316c-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="b316c-108">While – smyčky</span><span class="sxs-lookup"><span data-stu-id="b316c-108">While Loops</span></span>  
 <span data-ttu-id="b316c-109">`While`... `End While` konstrukce spustí sadu příkazů, tak dlouho, dokud podmínky zadané v `While` příkaz `True`.</span><span class="sxs-lookup"><span data-stu-id="b316c-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="b316c-110">Další informace najdete v tématu [při... End While – příkaz](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b316c-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="b316c-111">Do – smyčky</span><span class="sxs-lookup"><span data-stu-id="b316c-111">Do Loops</span></span>  
 <span data-ttu-id="b316c-112">`Do`... `Loop` konstrukce umožňuje otestovat podmínku na začátku nebo konci struktury smyčky.</span><span class="sxs-lookup"><span data-stu-id="b316c-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="b316c-113">Můžete také určit, zda opakování smyčky, přičemž zůstane podmínku `True` nebo dokud se nezmění `True`.</span><span class="sxs-lookup"><span data-stu-id="b316c-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="b316c-114">Další informace najdete v tématu [provést... Cykly příkaz](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b316c-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="b316c-115">Smyčky for</span><span class="sxs-lookup"><span data-stu-id="b316c-115">For Loops</span></span>  
 <span data-ttu-id="b316c-116">`For`... `Next` konstrukce provede smyčky sadu stanovený počet.</span><span class="sxs-lookup"><span data-stu-id="b316c-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="b316c-117">Používá proměnnou řízení smyčky, označované taky jako *čítač*, můžete sledovat opakování.</span><span class="sxs-lookup"><span data-stu-id="b316c-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="b316c-118">Zadejte počáteční a koncové hodnoty pro tento čítač a volitelně můžete zadat dobu, podle kterého jeho hodnota se zvyšuje z jednoho opakování na další.</span><span class="sxs-lookup"><span data-stu-id="b316c-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="b316c-119">Další informace najdete v tématu [pro... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b316c-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="b316c-120">Pro každý smyčky</span><span class="sxs-lookup"><span data-stu-id="b316c-120">For Each Loops</span></span>  
 <span data-ttu-id="b316c-121">`For Each`... `Next` konstrukce spustí sadu příkazů jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="b316c-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="b316c-122">Zadejte proměnnou řízení smyčky, ale nemáte k určení počáteční nebo koncové hodnoty pro ni.</span><span class="sxs-lookup"><span data-stu-id="b316c-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="b316c-123">Další informace najdete v tématu [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b316c-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b316c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b316c-124">See Also</span></span>  
 [<span data-ttu-id="b316c-125">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="b316c-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="b316c-126">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="b316c-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="b316c-127">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="b316c-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="b316c-128">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="b316c-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
