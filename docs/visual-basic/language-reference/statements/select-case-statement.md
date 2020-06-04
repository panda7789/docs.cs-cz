---
title: Select...Case – příkaz
ms.date: 07/20/2015
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
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404236"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="69be5-102">Select...Case – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69be5-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="69be5-103">Spustí jednu z několika skupin příkazů, v závislosti na hodnotě výrazu.</span><span class="sxs-lookup"><span data-stu-id="69be5-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69be5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69be5-104">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="69be5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="69be5-105">Parts</span></span>  
  
|<span data-ttu-id="69be5-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="69be5-106">Term</span></span>|<span data-ttu-id="69be5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="69be5-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="69be5-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="69be5-108">Required.</span></span> <span data-ttu-id="69be5-109">Vyjádření.</span><span class="sxs-lookup"><span data-stu-id="69be5-109">Expression.</span></span> <span data-ttu-id="69be5-110">Musí se vyhodnotit jako jeden ze základních datových typů ( `Boolean` , `Byte` ,, `Char` `Date` , `Double` , `Decimal` , `Integer` , `Long` ,,,, `Object` `SByte` `Short` `Single` , `String` ,, a `UInteger` `ULong` `UShort` ).</span><span class="sxs-lookup"><span data-stu-id="69be5-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="69be5-111">Vyžadováno v `Case` příkazu.</span><span class="sxs-lookup"><span data-stu-id="69be5-111">Required in a `Case` statement.</span></span> <span data-ttu-id="69be5-112">Seznam klauzulí výrazů, které představují hodnoty shody pro `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="69be5-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="69be5-113">Vícenásobné klauzule výrazu jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="69be5-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="69be5-114">Každá klauzule může mít jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="69be5-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="69be5-115">-   *Výraz1* `To` *Výraz2*</span><span class="sxs-lookup"><span data-stu-id="69be5-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="69be5-116">-[ `Is` ] *comparisonoperator* *výraz* ComparisonOperator</span><span class="sxs-lookup"><span data-stu-id="69be5-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="69be5-117">-   *vyjádření*</span><span class="sxs-lookup"><span data-stu-id="69be5-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="69be5-118">Pomocí `To` klíčového slova určete hranice rozsahu hodnot shody pro `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="69be5-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="69be5-119">Hodnota `expression1` musí být menší nebo rovna hodnotě `expression2` .</span><span class="sxs-lookup"><span data-stu-id="69be5-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="69be5-120">Použijte `Is` klíčové slovo s operátorem porovnání ( `=` , `<>` ,,, `<` `<=` `>` nebo `>=` ) a určete omezení pro hodnoty shody pro `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="69be5-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="69be5-121">Pokud `Is` klíčové slovo není zadáno, je automaticky vloženo před *ComparisonOperator*.</span><span class="sxs-lookup"><span data-stu-id="69be5-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="69be5-122">Formulář, který určuje pouze, `expression` se považuje za zvláštní případ `Is` formuláře, kde *ComparisonOperator* je rovnítko ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="69be5-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="69be5-123">Tento formulář je vyhodnocen jako `testexpression`  =  `expression` .</span><span class="sxs-lookup"><span data-stu-id="69be5-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="69be5-124">Výrazy v `expressionlist` můžou být libovolného datového typu, za předpokladu, že jsou implicitně převoditelné na typ `testexpression` a příslušné `comparisonoperator` jsou platné pro dva typy, se kterými se používá.</span><span class="sxs-lookup"><span data-stu-id="69be5-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="69be5-125">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="69be5-125">Optional.</span></span> <span data-ttu-id="69be5-126">Jeden nebo více příkazů, které následují za `Case` běhu, pokud `testexpression` odpovídají libovolné klauzuli v `expressionlist` .</span><span class="sxs-lookup"><span data-stu-id="69be5-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="69be5-127">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="69be5-127">Optional.</span></span> <span data-ttu-id="69be5-128">Jeden nebo více příkazů, které následují za `Case Else` běhu, pokud `testexpression` neodpovídají žádné klauzuli v `expressionlist` žádné z `Case` příkazů.</span><span class="sxs-lookup"><span data-stu-id="69be5-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="69be5-129">Ukončí definici `Select` konstrukce.... `Case`</span><span class="sxs-lookup"><span data-stu-id="69be5-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69be5-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69be5-130">Remarks</span></span>  
 <span data-ttu-id="69be5-131">Pokud `testexpression` odpovídá `Case` `expressionlist` klauzuli any, příkazy, které následují za tímto příkazem, se `Case` spustí až do následujícího `Case` `Case Else` příkazu, nebo `End Select` .</span><span class="sxs-lookup"><span data-stu-id="69be5-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="69be5-132">Řízení pak předá následujícímu příkazu `End Select` .</span><span class="sxs-lookup"><span data-stu-id="69be5-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="69be5-133">Pokud `testexpression` se shoduje s `expressionlist` klauzulí ve více než jedné `Case` klauzuli, spustí se jenom příkazy, které následují po první shodě.</span><span class="sxs-lookup"><span data-stu-id="69be5-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="69be5-134">`Case Else`Příkaz slouží k zavedení příkazu `elsestatements` ke spuštění, pokud není nalezena shoda mezi `testexpression` klauzulí a a `expressionlist` v žádném z ostatních `Case` příkazů.</span><span class="sxs-lookup"><span data-stu-id="69be5-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="69be5-135">I když to není vyžadováno, je vhodné mít `Case Else` příkaz ve vaší `Select Case` konstrukci pro zpracování nepředvídatelných `testexpression` hodnot.</span><span class="sxs-lookup"><span data-stu-id="69be5-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="69be5-136">Pokud `Case` `expressionlist` se neshoduje žádná klauzule `testexpression` a neexistuje žádný `Case Else` příkaz, ovládací prvek předá příkaz následujícímu příkazu `End Select` .</span><span class="sxs-lookup"><span data-stu-id="69be5-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="69be5-137">V každé klauzuli můžete použít více výrazů nebo rozsahů `Case` .</span><span class="sxs-lookup"><span data-stu-id="69be5-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="69be5-138">Například následující řádek je platný.</span><span class="sxs-lookup"><span data-stu-id="69be5-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="69be5-139">`Is`Klíčové slovo použité v `Case` `Case Else` příkazech a není stejné jako [operátor is](../operators/is-operator.md), který se používá pro porovnání odkazů na objekty.</span><span class="sxs-lookup"><span data-stu-id="69be5-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="69be5-140">Pro řetězce znaků lze zadat rozsahy a více výrazů.</span><span class="sxs-lookup"><span data-stu-id="69be5-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="69be5-141">V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který je přesně roven "jablk", má hodnotu mezi "NUTS" a "polévka" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem` .</span><span class="sxs-lookup"><span data-stu-id="69be5-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="69be5-142">Nastavení `Option Compare` může ovlivnit porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="69be5-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="69be5-143">V části jsou `Option Compare Text` řetězce "jablka" a "jablka" porovnány jako stejné, ale v nástroji `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="69be5-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69be5-144">`Case`Příkaz s více klauzulemi může vykazovat chování označované jako *krátkodobé okruhy*.</span><span class="sxs-lookup"><span data-stu-id="69be5-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="69be5-145">Visual Basic vyhodnocuje klauzule zleva doprava a pokud jedna vytvoří shodu s `testexpression` , zbývající klauzule nejsou vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="69be5-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="69be5-146">Krátkodobé okruhy mohou zvýšit výkon, ale může dojít k neočekávaným výsledkům, pokud očekáváte, že se každý výraz v `expressionlist` má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="69be5-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="69be5-147">Další informace o krátkodobém okruhu naleznete v tématu [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="69be5-147">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="69be5-148">Pokud kód v rámci `Case` `Case Else` bloku příkazu nebo není nutné spouštět žádné další příkazy v bloku, může tento blok opustit pomocí `Exit Select` příkazu.</span><span class="sxs-lookup"><span data-stu-id="69be5-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="69be5-149">Tím se ovládací prvek přenáší hned na následující příkaz `End Select` .</span><span class="sxs-lookup"><span data-stu-id="69be5-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="69be5-150">`Select Case`konstrukce můžou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="69be5-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="69be5-151">Každá vnořená `Select Case` konstrukce musí mít `End Select` příkaz, který musí být zcela obsažen v rámci jednoho `Case` nebo více `Case Else` příkazů bloku vnější `Select Case` konstrukce, v rámci které je vnořena.</span><span class="sxs-lookup"><span data-stu-id="69be5-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69be5-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="69be5-152">Example</span></span>  
 <span data-ttu-id="69be5-153">V následujícím příkladu je použita `Select Case` konstrukce pro zápis řádku, který odpovídá hodnotě proměnné `number` .</span><span class="sxs-lookup"><span data-stu-id="69be5-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="69be5-154">Druhý `Case` příkaz obsahuje hodnotu, která odpovídá aktuální hodnotě `number` , takže příkaz, který zapisuje "mezi 6 a 8 včetně", se spouští.</span><span class="sxs-lookup"><span data-stu-id="69be5-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="69be5-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="69be5-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="69be5-156">Příkaz end</span><span class="sxs-lookup"><span data-stu-id="69be5-156">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="69be5-157">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="69be5-157">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="69be5-158">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="69be5-158">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="69be5-159">Exit – příkaz</span><span class="sxs-lookup"><span data-stu-id="69be5-159">Exit Statement</span></span>](exit-statement.md)
