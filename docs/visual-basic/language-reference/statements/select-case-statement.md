---
title: "Select...Case – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="b7582-102">Select...Case – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7582-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="b7582-103">Používá jednu z několika skupin příkazů, v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="b7582-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7582-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7582-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="b7582-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b7582-105">Parts</span></span>  
  
|<span data-ttu-id="b7582-106">Termín</span><span class="sxs-lookup"><span data-stu-id="b7582-106">Term</span></span>|<span data-ttu-id="b7582-107">Definice</span><span class="sxs-lookup"><span data-stu-id="b7582-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="b7582-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b7582-108">Required.</span></span> <span data-ttu-id="b7582-109">Výraz.</span><span class="sxs-lookup"><span data-stu-id="b7582-109">Expression.</span></span> <span data-ttu-id="b7582-110">Musí být vyhodnocen jako jeden z základní datové typy (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, a `UShort`).</span><span class="sxs-lookup"><span data-stu-id="b7582-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="b7582-111">V požadován `Case` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b7582-111">Required in a `Case` statement.</span></span> <span data-ttu-id="b7582-112">Seznam výraz klauzule představující shody hodnoty pro `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="b7582-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="b7582-113">Více klauzulí výraz se oddělují čárkami.</span><span class="sxs-lookup"><span data-stu-id="b7582-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="b7582-114">Každý klauzule můžete provést jednu z následujících podob:</span><span class="sxs-lookup"><span data-stu-id="b7582-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="b7582-115">-   *Expression1* `To` *Výraz2*</span><span class="sxs-lookup"><span data-stu-id="b7582-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="b7582-116">-[ `Is` ] *porovnávací operátor* *výraz*</span><span class="sxs-lookup"><span data-stu-id="b7582-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="b7582-117">-   *výraz*</span><span class="sxs-lookup"><span data-stu-id="b7582-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="b7582-118">Použití `To` – klíčové slovo hranice rozsahu odpovídal zadat hodnoty pro `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="b7582-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="b7582-119">Hodnota `expression1` musí být menší než nebo rovna hodnotě `expression2`.</span><span class="sxs-lookup"><span data-stu-id="b7582-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="b7582-120">Použití `Is` – klíčové slovo pomocí operátoru porovnání (`=`, `<>`, `<`, `<=`, `>`, nebo `>=`) nastavit omezení u shody hodnoty pro `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="b7582-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="b7582-121">Pokud `Is` – klíčové slovo není zadána, bude automaticky vložen před *porovnávací operátor*.</span><span class="sxs-lookup"><span data-stu-id="b7582-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="b7582-122">Formulář zadání pouze `expression` je považován za zvláštní případ `Is` formuláři kde *porovnávací operátor* je znak rovná se (`=`).</span><span class="sxs-lookup"><span data-stu-id="b7582-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="b7582-123">Tento formulář je vyhodnoceno jako `testexpression`  =  `expression`.</span><span class="sxs-lookup"><span data-stu-id="b7582-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="b7582-124">Výrazy v `expressionlist` mohou být jakéhokoli typu dat předpokladu, že jsou implicitně převést na typ `testexpression` a odpovídající `comparisonoperator` je platný pro dva typy je používán s.</span><span class="sxs-lookup"><span data-stu-id="b7582-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="b7582-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b7582-125">Optional.</span></span> <span data-ttu-id="b7582-126">Jeden nebo více následujících příkazů `Case` že spuštění Pokud `testexpression` odpovídá všechny klauzule v `expressionlist`.</span><span class="sxs-lookup"><span data-stu-id="b7582-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="b7582-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b7582-127">Optional.</span></span> <span data-ttu-id="b7582-128">Jeden nebo více následujících příkazů `Case Else` že spuštění Pokud `testexpression` neodpovídá žádné klauzule v `expressionlist` každého `Case` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b7582-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="b7582-129">Ukončí definice `Select`... `Case` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="b7582-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7582-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7582-130">Remarks</span></span>  
 <span data-ttu-id="b7582-131">Pokud `testexpression` odpovídá některému `Case` `expressionlist` klauzuli, která následující příkazy `Case` příkaz spustit na další `Case`, `Case Else`, nebo `End Select` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b7582-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="b7582-132">Řízení potom předává pro následující příkaz `End Select`.</span><span class="sxs-lookup"><span data-stu-id="b7582-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="b7582-133">Pokud `testexpression` odpovídá `expressionlist` klauzule ve více než jeden `Case` klauzuli spustit jenom příkazy následující na první shodu.</span><span class="sxs-lookup"><span data-stu-id="b7582-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="b7582-134">`Case Else` Příkaz se používá k zavedení `elsestatements` ke spouštění, pokud není nalezena žádná shoda mezi `testexpression` a `expressionlist` klauzule některý z dalších `Case` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b7582-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="b7582-135">Ačkoli to není vyžadováno, je vhodné mít `Case Else` příkaz v vaše `Select Case` konstrukce pro zpracování nepředpokládaného `testexpression` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b7582-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="b7582-136">Pokud žádné `Case` `expressionlist` klauzule odpovídá `testexpression` a neexistuje žádné `Case Else` prohlášení, předává řízení pro následující příkaz `End Select`.</span><span class="sxs-lookup"><span data-stu-id="b7582-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="b7582-137">Můžete použít více výrazů ani rozsahů v každé `Case` klauzule.</span><span class="sxs-lookup"><span data-stu-id="b7582-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="b7582-138">Například následující řádek je platný.</span><span class="sxs-lookup"><span data-stu-id="b7582-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="b7582-139">`Is` Klíčové slovo používané v `Case` a `Case Else` příkazy není stejný jako [je operátor](../../../visual-basic/language-reference/operators/is-operator.md), který se používá pro porovnání odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="b7582-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="b7582-140">Můžete určit rozsahy a více výrazů pro řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="b7582-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="b7582-141">V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který se rovná "jablka", má hodnotu mezi "nuts" a "polévky" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem`.</span><span class="sxs-lookup"><span data-stu-id="b7582-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="b7582-142">Nastavení `Option Compare` může ovlivnit porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="b7582-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="b7582-143">V části `Option Compare Text`, porovnat řetězce "Jablka" a "jablka" jako rovnocenné, ale v části `Option Compare Binary`, ne.</span><span class="sxs-lookup"><span data-stu-id="b7582-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7582-144">A `Case` příkaz s více klauzulí může vykazovat chování známé jako *krátká smyčka*.</span><span class="sxs-lookup"><span data-stu-id="b7582-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="b7582-145">Visual Basic vyhodnotí klauzule zleva doprava a pokud vytváří shody s `testexpression`, zbývající klauzule nevyhodnocují.</span><span class="sxs-lookup"><span data-stu-id="b7582-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="b7582-146">Krátká smyčka může zlepšit výkon, ale může způsobit neočekávaný výsledek, pokud očekáváte každých výrazu v `expressionlist` k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b7582-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="b7582-147">Další informace o krátká smyčka najdete v tématu [logické výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b7582-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="b7582-148">Pokud kód v rámci `Case` nebo `Case Else` blok příkazu není nutné spustit všechny více příkazy v bloku, blok ho můžete ukončit pomocí `Exit Select` příkaz.</span><span class="sxs-lookup"><span data-stu-id="b7582-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="b7582-149">Toto okamžitě převede řízení pro následující příkaz `End Select`.</span><span class="sxs-lookup"><span data-stu-id="b7582-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="b7582-150">`Select Case`konstrukce mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="b7582-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="b7582-151">Všechny vnořené `Select Case` konstrukce musí mít odpovídající `End Select` příkaz a musí být zcela obsažen v rámci jednoho `Case` nebo `Case Else` příkaz blok vnější `Select Case` konstrukce, ve kterém je vnořený.</span><span class="sxs-lookup"><span data-stu-id="b7582-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7582-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7582-152">Example</span></span>  
 <span data-ttu-id="b7582-153">Následující příklad používá `Select Case` konstrukce k zápisu řádku odpovídající hodnotě proměnné `number`.</span><span class="sxs-lookup"><span data-stu-id="b7582-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="b7582-154">Druhý `Case` příkaz obsahuje hodnotu, která odpovídá aktuální hodnota `number`, takže příkaz, který zapíše "6 až 8, včetně" spustí.</span><span class="sxs-lookup"><span data-stu-id="b7582-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b7582-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7582-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [<span data-ttu-id="b7582-156">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7582-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="b7582-157">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7582-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="b7582-158">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7582-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="b7582-159">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7582-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
