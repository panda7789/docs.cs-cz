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
ms.openlocfilehash: f0df649c4be50e9cadd51258c89137b68b4ffe22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963201"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="88a91-102">Struktury rozhodování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88a91-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="88a91-103">Visual Basic umožňuje testovat podmínky a provádět různé operace v závislosti na výsledcích tohoto testu.</span><span class="sxs-lookup"><span data-stu-id="88a91-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="88a91-104">Můžete testovat podmínku true nebo false, pro různé hodnoty výrazu nebo pro různé výjimky vygenerované při spuštění řady příkazů.</span><span class="sxs-lookup"><span data-stu-id="88a91-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="88a91-105">Následující ilustrace znázorňuje rozhodovací strukturu, která testuje podmínku na hodnotu true a provede různé akce v závislosti na tom, zda je hodnota true nebo false.</span><span class="sxs-lookup"><span data-stu-id="88a91-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Vývojový diagram if... Pak... Jinak konstrukce.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="88a91-107">Pokud... Pak... Konstrukce else</span><span class="sxs-lookup"><span data-stu-id="88a91-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="88a91-108">`If...Then...Else`konstrukce umožňují otestovat jednu nebo více podmínek a spustit jeden nebo více příkazů v závislosti na každé podmínce.</span><span class="sxs-lookup"><span data-stu-id="88a91-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="88a91-109">Můžete testovat podmínky a provádět akce následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="88a91-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="88a91-110">Spustit jeden nebo více příkazů, pokud je podmínka`True`</span><span class="sxs-lookup"><span data-stu-id="88a91-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="88a91-111">Spustit jeden nebo více příkazů, pokud je podmínka`False`</span><span class="sxs-lookup"><span data-stu-id="88a91-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="88a91-112">Spustit některé příkazy, pokud je `True` podmínka, a další, pokud jsou`False`</span><span class="sxs-lookup"><span data-stu-id="88a91-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="88a91-113">Test další podmínky, pokud je předchozí podmínka`False`</span><span class="sxs-lookup"><span data-stu-id="88a91-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="88a91-114">Struktura ovládacího prvku, která nabízí všechny tyto možnosti, je [if... Pak... ELSE – příkaz](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88a91-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="88a91-115">Pokud máte pouze jeden test a jeden příkaz ke spuštění, můžete použít jednořádkových verzí.</span><span class="sxs-lookup"><span data-stu-id="88a91-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="88a91-116">Pokud máte složitější sadu podmínek a akcí, můžete použít víceřádkovou verzi.</span><span class="sxs-lookup"><span data-stu-id="88a91-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="88a91-117">Vybrat... Konstrukce případu</span><span class="sxs-lookup"><span data-stu-id="88a91-117">Select...Case Construction</span></span>  
 <span data-ttu-id="88a91-118">`Select...Case` Konstrukce umožňuje vyhodnotit výraz jednou a spouštět různé sady příkazů na základě různých možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="88a91-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="88a91-119">Další informace najdete v tématu věnovaném [výběru... Příkaz Case](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88a91-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="88a91-120">Zkusit... Zachytit... Nakonec konstrukce</span><span class="sxs-lookup"><span data-stu-id="88a91-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="88a91-121">`Try...Catch...Finally`konstrukce umožňují spustit sadu příkazů v prostředí, které si zachovají řízení, pokud některý z vašich příkazů způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="88a91-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="88a91-122">Můžete provádět různé akce pro různé výjimky.</span><span class="sxs-lookup"><span data-stu-id="88a91-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="88a91-123">Volitelně můžete zadat blok kódu, který se spustí před ukončením celé `Try...Catch...Finally` konstrukce bez ohledu na to, co se děje.</span><span class="sxs-lookup"><span data-stu-id="88a91-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="88a91-124">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88a91-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88a91-125">U mnoha řídicích struktur se při kliknutí na klíčové slovo zvýrazní všechna klíčová slova ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="88a91-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="88a91-126">`If` Například při kliknutí `If...Then...Else` na `Then` `ElseIf` `End If` konstrukci jsou zvýrazněny všechny`Else`instance,,, a v konstrukci. `If`</span><span class="sxs-lookup"><span data-stu-id="88a91-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="88a91-127">Chcete-li přejít na další nebo předchozí zvýrazněné klíčové slovo, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru.</span><span class="sxs-lookup"><span data-stu-id="88a91-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a91-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88a91-128">See also</span></span>

- [<span data-ttu-id="88a91-129">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="88a91-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="88a91-130">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="88a91-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="88a91-131">Ostatní řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="88a91-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="88a91-132">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="88a91-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="88a91-133">Operátor If</span><span class="sxs-lookup"><span data-stu-id="88a91-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
