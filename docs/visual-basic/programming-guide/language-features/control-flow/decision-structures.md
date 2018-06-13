---
title: Struktury rozhodování (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 1ede40d196b470a351aca4c60b33f074df14b86a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648194"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="3b6ae-102">Struktury rozhodování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b6ae-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="3b6ae-103">Visual Basic umožňuje testovacích podmínkách a provádět různé operace v závislosti na výsledky testu.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="3b6ae-104">Můžete otestovat podmínku true nebo false, pro různé hodnoty výrazu, nebo pro různé výjimky, které jsou generovány, pokud provádějí sérii příkazů.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="3b6ae-105">Následující obrázek znázorňuje rozhodovací strukturu, která se testuje podmínku se skutečnou a trvá různé akce v závislosti na tom, jestli je true nebo false.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="3b6ae-106">![Vývojový diagram Pokud... Potom... Else konstrukce](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse –")</span><span class="sxs-lookup"><span data-stu-id="3b6ae-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="3b6ae-107">Pořízení různé akce, pokud je podmínka true a kdy je false</span><span class="sxs-lookup"><span data-stu-id="3b6ae-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="3b6ae-108">If... Potom... Else konstrukce</span><span class="sxs-lookup"><span data-stu-id="3b6ae-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="3b6ae-109">`If...Then...Else` konstrukce umožňuje otestovat pro jednu nebo víc podmínek a spustit jeden nebo více příkazů v závislosti na každé podmínky.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="3b6ae-110">Můžete si otestovat podmínky a kroky následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="3b6ae-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="3b6ae-111">Pokud je podmínka spuštění jeden nebo více příkazů `True`</span><span class="sxs-lookup"><span data-stu-id="3b6ae-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="3b6ae-112">Pokud je podmínka spuštění jeden nebo více příkazů `False`</span><span class="sxs-lookup"><span data-stu-id="3b6ae-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="3b6ae-113">Pokud je podmínka spuštění některé příkazy `True` a jiné, pokud je `False`</span><span class="sxs-lookup"><span data-stu-id="3b6ae-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="3b6ae-114">Pokud je předběžnou podmínku otestovat další podmínky `False`</span><span class="sxs-lookup"><span data-stu-id="3b6ae-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="3b6ae-115">Ovládací prvek struktura, která nabízí tyto možnosti je [Pokud... Potom... Else – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b6ae-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="3b6ae-116">Pokud máte pouze jeden test a jeden příkaz ke spuštění, můžete použít verzi jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="3b6ae-117">Pokud máte složitější sadu podmínek a akcí, můžete použít verzi více řádků.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="3b6ae-118">Vyberte... Case konstrukce</span><span class="sxs-lookup"><span data-stu-id="3b6ae-118">Select...Case Construction</span></span>  
 <span data-ttu-id="3b6ae-119">`Select...Case` Konstrukce umožňuje vyhodnocení výrazu jednou a spouštět různé sady příkazů na základě různých možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="3b6ae-120">Další informace najdete v tématu [vyberte... Příkaz případ](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b6ae-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="3b6ae-121">Try... Catch... Nakonec konstrukce</span><span class="sxs-lookup"><span data-stu-id="3b6ae-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="3b6ae-122">`Try...Catch...Finally` konstrukce umožňují spustit sadu příkazů v prostředí, které zachovává řízení, pokud kterákoli vaší příkazů dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="3b6ae-123">Můžete provádět různé akce pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="3b6ae-124">Volitelně můžete zadat blok kódu, který se spustí před ukončete celek `Try...Catch...Finally` konstrukce, bez ohledu na to, co se stane.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="3b6ae-125">Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b6ae-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b6ae-126">Pro mnoho řídicí struktury po kliknutí na tlačítko klíčové slovo, všechny klíčová slova ve struktuře jsou vyznačené.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="3b6ae-127">Například když kliknete na tlačítko `If` v `If...Then...Else` konstrukce, všechny instance `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou vyznačené při sestavování.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="3b6ae-128">Chcete-li přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="3b6ae-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6ae-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b6ae-129">See Also</span></span>  
 [<span data-ttu-id="3b6ae-130">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="3b6ae-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="3b6ae-131">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="3b6ae-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="3b6ae-132">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="3b6ae-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="3b6ae-133">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="3b6ae-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="3b6ae-134">Operátor If</span><span class="sxs-lookup"><span data-stu-id="3b6ae-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
