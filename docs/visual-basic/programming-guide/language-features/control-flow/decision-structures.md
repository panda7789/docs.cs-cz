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
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318933"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="7118f-102">Struktury rozhodování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7118f-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="7118f-103">Visual Basic umožňuje podmínky testu a provádět různé operace v závislosti na výsledcích testu.</span><span class="sxs-lookup"><span data-stu-id="7118f-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="7118f-104">Můžete otestovat na hodnotu true nebo false pro různé hodnoty výrazu, nebo pro různé výjimky, které jsou generovány, pokud provedete sérii tvrzení, podmínku.</span><span class="sxs-lookup"><span data-stu-id="7118f-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="7118f-105">Následující ilustrace znázorňuje strukturu rozhodnutí, která otestuje podmínku je true a má různé akce v závislosti na tom, zda je hodnota true nebo false.</span><span class="sxs-lookup"><span data-stu-id="7118f-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Vývojový diagram If... Potom... Ostatní konstrukce.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="7118f-107">If...Then...Else Construction</span><span class="sxs-lookup"><span data-stu-id="7118f-107">If...Then...Else Construction</span></span>  
 `If...Then...Else` <span data-ttu-id="7118f-108">konstrukce umožňují test pro jednu nebo více podmínek a spuštění jednoho nebo více příkazů v závislosti na každé podmínky.</span><span class="sxs-lookup"><span data-stu-id="7118f-108">constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="7118f-109">Můžete otestovat podmínek a akcí následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="7118f-109">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="7118f-110">Spustit jeden nebo více příkazů, pokud je podmínka</span><span class="sxs-lookup"><span data-stu-id="7118f-110">Run one or more statements if a condition is</span></span> `True`  
  
-   <span data-ttu-id="7118f-111">Spustit jeden nebo více příkazů, pokud je podmínka</span><span class="sxs-lookup"><span data-stu-id="7118f-111">Run one or more statements if a condition is</span></span> `False`  
  
-   <span data-ttu-id="7118f-112">Spustit některé příkazy, pokud je podmínka `True` a dalších jde</span><span class="sxs-lookup"><span data-stu-id="7118f-112">Run some statements if a condition is `True` and others if it is</span></span> `False`  
  
-   <span data-ttu-id="7118f-113">Vyzkoušejte další podmínky, pokud je předběžnou podmínku</span><span class="sxs-lookup"><span data-stu-id="7118f-113">Test an additional condition if a prior condition is</span></span> `False`  
  
 <span data-ttu-id="7118f-114">Je řídicí struktura, která nabízí tyto možnosti [Pokud... Potom... Else – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7118f-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="7118f-115">Jednořádkový verze můžete použít, pokud máte pouze jeden test a jeden příkaz ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="7118f-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="7118f-116">Pokud máte složitější sadu podmínek a akcí, můžete použít verzi více řádků.</span><span class="sxs-lookup"><span data-stu-id="7118f-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="7118f-117">Vyberte... Případu konstrukce</span><span class="sxs-lookup"><span data-stu-id="7118f-117">Select...Case Construction</span></span>  
 <span data-ttu-id="7118f-118">`Select...Case` Konstrukce umožňuje vyhodnocení výrazu jednou a spustit jinou sadu příkazů na základě různých možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="7118f-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="7118f-119">Další informace najdete v tématu [vyberte... Case – příkaz](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7118f-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="7118f-120">Try... Catch... Nakonec konstrukce</span><span class="sxs-lookup"><span data-stu-id="7118f-120">Try...Catch...Finally Construction</span></span>  
 `Try...Catch...Finally` <span data-ttu-id="7118f-121">konstrukce umožňují spustit sadu příkazů v rámci prostředí, který bude mít ovládací prvek, pokud některý z výpisy dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="7118f-121">constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="7118f-122">Můžete provádět různé akce pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="7118f-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="7118f-123">Volitelně můžete zadat blok kódu, který se spustí před ukončením celé `Try...Catch...Finally` konstrukce, bez ohledu na to, co se stane.</span><span class="sxs-lookup"><span data-stu-id="7118f-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="7118f-124">Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7118f-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7118f-125">Pro mnoho řídících struktur po kliknutí na klíčové slovo, všechna klíčová slova ve struktuře jsou zvýrazněné.</span><span class="sxs-lookup"><span data-stu-id="7118f-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="7118f-126">Například po kliknutí na `If` v `If...Then...Else` konstrukce, všechny výskyty `If`, `Then`, `ElseIf`, `Else`, a `End If` jsou zvýrazněné v procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="7118f-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="7118f-127">Přesunout další nebo předchozí zvýrazněný – klíčové slovo, stiskněte kombinaci kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="7118f-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7118f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7118f-128">See also</span></span>

- [<span data-ttu-id="7118f-129">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="7118f-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="7118f-130">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="7118f-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="7118f-131">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="7118f-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="7118f-132">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="7118f-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7118f-133">If – operátor</span><span class="sxs-lookup"><span data-stu-id="7118f-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
