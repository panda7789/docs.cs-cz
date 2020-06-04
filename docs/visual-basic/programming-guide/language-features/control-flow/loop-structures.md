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
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403512"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="00078-102">Struktury smyčky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00078-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="00078-103">Struktury smyčky Visual Basic umožňují spustit jeden nebo více řádků kódu opakovaně.</span><span class="sxs-lookup"><span data-stu-id="00078-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="00078-104">Příkazy lze opakovat ve struktuře smyčky, dokud není podmínka, `True` dokud není podmínka `False` , zadaný počet opakování nebo jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="00078-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="00078-105">Následující ilustrace znázorňuje strukturu smyčky, která spouští sadu příkazů, dokud podmínka nebude pravdivá:</span><span class="sxs-lookup"><span data-stu-id="00078-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Vývojový diagram, který zobrazuje do... Do smyčky.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="00078-107">Cykly ve smyčce</span><span class="sxs-lookup"><span data-stu-id="00078-107">While Loops</span></span>  
 <span data-ttu-id="00078-108">`While`Konstrukce... `End While` spouští sadu příkazů, pokud je podmínka zadaná v `While` příkazu `True` .</span><span class="sxs-lookup"><span data-stu-id="00078-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="00078-109">Další informace najdete v části [while... Příkaz End While](../../../language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="00078-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="00078-110">Do smyček</span><span class="sxs-lookup"><span data-stu-id="00078-110">Do Loops</span></span>  
 <span data-ttu-id="00078-111">`Do`Konstrukce... `Loop` umožňuje testovat podmínku buď na začátku, nebo na konci struktury smyčky.</span><span class="sxs-lookup"><span data-stu-id="00078-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="00078-112">Můžete také určit, jestli se má opakovat smyčka, když podmínka zůstane `True` nebo dokud se nespustí `True` .</span><span class="sxs-lookup"><span data-stu-id="00078-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="00078-113">Další informace najdete v části [do... Příkaz LOOP](../../../language-reference/statements/do-loop-statement.md)</span><span class="sxs-lookup"><span data-stu-id="00078-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="00078-114">Smyčka for</span><span class="sxs-lookup"><span data-stu-id="00078-114">For Loops</span></span>  
 <span data-ttu-id="00078-115">`For`Konstrukce... `Next` provádí smyčku v nastaveném počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="00078-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="00078-116">K udržení přehledu opakování používá proměnnou ovládacího prvku smyčky, která se označuje také jako *čítač*.</span><span class="sxs-lookup"><span data-stu-id="00078-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="00078-117">Zadejte počáteční a koncové hodnoty pro tento čítač a můžete volitelně zadat hodnotu, o kterou se zvýší z jednoho opakování na další.</span><span class="sxs-lookup"><span data-stu-id="00078-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="00078-118">Další informace najdete v tématu [... Další příkaz](../../../language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="00078-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="00078-119">Pro každou smyčku</span><span class="sxs-lookup"><span data-stu-id="00078-119">For Each Loops</span></span>  
 <span data-ttu-id="00078-120">`For Each`Konstrukce... `Next` spouští sadu příkazů jednou pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="00078-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="00078-121">Zadáte řídicí proměnnou smyčky, ale nemusíte určit počáteční nebo koncové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="00078-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="00078-122">Další informace najdete v tématu [for each... Další příkaz](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="00078-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00078-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="00078-123">See also</span></span>

- [<span data-ttu-id="00078-124">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="00078-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="00078-125">Struktury rozhodování</span><span class="sxs-lookup"><span data-stu-id="00078-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="00078-126">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="00078-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="00078-127">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="00078-127">Nested Control Structures</span></span>](nested-control-structures.md)
