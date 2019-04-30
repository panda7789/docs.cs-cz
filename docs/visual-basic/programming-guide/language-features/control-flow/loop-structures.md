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
ms.openlocfilehash: 56165eecce5e73c4e06235dac1691774fb39b794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906855"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="fa25d-102">Struktury smyčky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa25d-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="fa25d-103">Struktury smyčky v jazyce Visual Basic umožňují opakovaně spustit jeden nebo více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="fa25d-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="fa25d-104">Příkazy ve smyčce struktura můžete opakovat, dokud je podmínka `True`, dokud je podmínka `False`, zadaný počet opakování, nebo jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="fa25d-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="fa25d-105">Struktury smyčky, na kterém běží sada příkazů, dokud se podmínka stane pravdivou naleznete na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="fa25d-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Vývojový diagram zobrazující DNT... Až do smyčky.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="fa25d-107">Smyčky while</span><span class="sxs-lookup"><span data-stu-id="fa25d-107">While Loops</span></span>  
 <span data-ttu-id="fa25d-108">`While`... `End While` konstrukce spustí sadu příkazů tak dlouho, dokud podmínka podle `While` příkaz je `True`.</span><span class="sxs-lookup"><span data-stu-id="fa25d-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="fa25d-109">Další informace najdete v tématu [během... End While – příkaz](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fa25d-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="fa25d-110">Do Loops</span><span class="sxs-lookup"><span data-stu-id="fa25d-110">Do Loops</span></span>  
 <span data-ttu-id="fa25d-111">`Do`... `Loop` konstrukce využijete k otestování podmínky na začátku nebo konci struktury smyčky.</span><span class="sxs-lookup"><span data-stu-id="fa25d-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="fa25d-112">Můžete také určit, jestli se má opakování cyklu, zatímco zůstane podmínka `True` nebo dokud nebude `True`.</span><span class="sxs-lookup"><span data-stu-id="fa25d-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="fa25d-113">Další informace najdete v tématu [udělat... Smyčky příkaz](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fa25d-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="fa25d-114">Smyčky for</span><span class="sxs-lookup"><span data-stu-id="fa25d-114">For Loops</span></span>  
 <span data-ttu-id="fa25d-115">`For`... `Next` konstrukce provádí smyčky do sady počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="fa25d-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="fa25d-116">Použije řídicí proměnná smyčky for, zkratka *čítač*, můžete sledovat opakování.</span><span class="sxs-lookup"><span data-stu-id="fa25d-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="fa25d-117">Zadejte počáteční a koncové hodnoty tohoto čítače, a volitelně můžete zadat dobu, podle kterého jeho hodnota se zvyšuje z jednoho opakování na další.</span><span class="sxs-lookup"><span data-stu-id="fa25d-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="fa25d-118">Další informace najdete v tématu [pro... Další příkaz](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fa25d-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="fa25d-119">Smyčky For Each</span><span class="sxs-lookup"><span data-stu-id="fa25d-119">For Each Loops</span></span>  
 <span data-ttu-id="fa25d-120">`For Each`... `Next` konstrukce spustí sadu příkazů jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="fa25d-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="fa25d-121">Zadat řídicí proměnná smyčky for, ale nemáte k určení počáteční nebo koncovou hodnotou pro něj.</span><span class="sxs-lookup"><span data-stu-id="fa25d-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="fa25d-122">Další informace najdete v tématu [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fa25d-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa25d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa25d-123">See also</span></span>

- [<span data-ttu-id="fa25d-124">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="fa25d-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="fa25d-125">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="fa25d-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="fa25d-126">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="fa25d-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="fa25d-127">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="fa25d-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
