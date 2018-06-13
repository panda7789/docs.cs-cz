---
title: for (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 2c099411499c6ca8396c55955bdc634e48caf621
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306524"
---
# <a name="for-c-reference"></a><span data-ttu-id="d7878-102">pro (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d7878-102">for (C# reference)</span></span>

<span data-ttu-id="d7878-103">Pomocí `for` smyčku, můžete spustit příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`.</span><span class="sxs-lookup"><span data-stu-id="d7878-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="d7878-104">Tento druh smyčky je užitečný pro iterování přes pole a pro jiné aplikace, ve kterých víte předem kolikrát chcete, aby k iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>
  
## <a name="example"></a><span data-ttu-id="d7878-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7878-105">Example</span></span>

<span data-ttu-id="d7878-106">V následujícím příkladu, hodnota `i` je zapsána do konzoly a při každé iteraci smyčky zvýší o 1:</span><span class="sxs-lookup"><span data-stu-id="d7878-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop:</span></span>
  
[!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]
  
<span data-ttu-id="d7878-107">[Pro příkaz](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) v předchozím příkladu provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="d7878-107">The [for statement](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) in the previous example performs the following actions:</span></span>
  
1.  <span data-ttu-id="d7878-108">První, počáteční hodnota proměnné `i` je vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="d7878-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="d7878-109">Tento krok se stane pouze jednou, bez ohledu na to, jak mnohokrát opakuje smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="d7878-110">Tato inicializace si můžete představit jako situaci mimo proces opakování.</span><span class="sxs-lookup"><span data-stu-id="d7878-110">You can think of this initialization as happening outside the looping process.</span></span>
  
2.  <span data-ttu-id="d7878-111">Při vyhodnocení podmínky (`i <= 5`), hodnota `i` se porovná s 5.</span><span class="sxs-lookup"><span data-stu-id="d7878-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>
  
    -   <span data-ttu-id="d7878-112">Pokud `i` je menší než nebo rovna 5, je podmínka vyhodnocena jako `true`, a dojde k následujícím akcím.</span><span class="sxs-lookup"><span data-stu-id="d7878-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="d7878-113">`Console.WriteLine` Příkaz do těla smyčky zobrazuje hodnotu `i`.</span><span class="sxs-lookup"><span data-stu-id="d7878-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="d7878-114">Hodnota `i` se zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="d7878-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="d7878-115">Smyčky vrátí začátek krok 2: vyhodnocení podmínky znovu.</span><span class="sxs-lookup"><span data-stu-id="d7878-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="d7878-116">Pokud `i` je větší než 5, je podmínka vyhodnocena jako `false`, a ukončení smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
<span data-ttu-id="d7878-117">Všimněte si, že, pokud počáteční hodnota `i` je větší než 5, do těla smyčky nefunguje i jednou.</span><span class="sxs-lookup"><span data-stu-id="d7878-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>

## <a name="sections-of-a-for-statement"></a><span data-ttu-id="d7878-118">Části pro příkaz</span><span class="sxs-lookup"><span data-stu-id="d7878-118">Sections of a for statement</span></span>
  
<span data-ttu-id="d7878-119">Každý [pro příkaz](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) definuje *inicializátoru*, *podmínku*, a *iterator* oddíly.</span><span class="sxs-lookup"><span data-stu-id="d7878-119">Every [for statement](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) defines *initializer*, *condition*, and *iterator* sections.</span></span> <span data-ttu-id="d7878-120">Tyto části obvykle určit počet opakování iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-120">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
<span data-ttu-id="d7878-121">V částech slouží k následujícím účelům:</span><span class="sxs-lookup"><span data-stu-id="d7878-121">The sections serve the following purposes:</span></span>
  
-   <span data-ttu-id="d7878-122">V části inicializátoru nastaví počáteční podmínky.</span><span class="sxs-lookup"><span data-stu-id="d7878-122">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="d7878-123">Příkazy v této části spustit jenom jednou před zadáním smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-123">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="d7878-124">V části může obsahovat pouze jednu z následujících dvou možností.</span><span class="sxs-lookup"><span data-stu-id="d7878-124">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="d7878-125">Deklarace a inicializace proměnné místní smyčky, jak ukazuje příklad první (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="d7878-125">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="d7878-126">Proměnná je místní pro smyčky a není přístupný z mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="d7878-126">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="d7878-127">Nula nebo více příkaz expressons z následujícího seznamu, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="d7878-127">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="d7878-128">[přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7878-128">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="d7878-129">volání metody</span><span class="sxs-lookup"><span data-stu-id="d7878-129">invocation of a method</span></span>  
  
        -   <span data-ttu-id="d7878-130">předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="d7878-130">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="d7878-131">předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="d7878-131">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="d7878-132">Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="d7878-132">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="d7878-133">[await](../../../csharp/language-reference/keywords/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="d7878-133">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="d7878-134">Podmínka oddíl obsahuje logický výraz, který se vyhodnotí k určení, zda smyčky musí ukončit nebo měli znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="d7878-134">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="d7878-135">Iterator oddíl definuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-135">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="d7878-136">Iterator obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:</span><span class="sxs-lookup"><span data-stu-id="d7878-136">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="d7878-137">[přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7878-137">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="d7878-138">volání metody</span><span class="sxs-lookup"><span data-stu-id="d7878-138">invocation of a method</span></span>  
  
    -   <span data-ttu-id="d7878-139">předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo `i++`</span><span class="sxs-lookup"><span data-stu-id="d7878-139">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="d7878-140">předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo `i--`</span><span class="sxs-lookup"><span data-stu-id="d7878-140">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="d7878-141">Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="d7878-141">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="d7878-142">[await](../../../csharp/language-reference/keywords/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="d7878-142">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="d7878-143">Do těla smyčky se skládá z příkazu, prázdný příkaz nebo blok příkazů, které vytvoříte uzavřením nula nebo více příkazů do složených závorek.</span><span class="sxs-lookup"><span data-stu-id="d7878-143">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="d7878-144">Můžete rozdělit mimo `for` smyčky pomocí [zalomení](../../../csharp/language-reference/keywords/break.md) – klíčové slovo, nebo můžete do další iterace krok pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d7878-144">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="d7878-145">Také můžete ukončit všechny smyčky pomocí [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="d7878-145">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
<span data-ttu-id="d7878-146">V prvním příkladu v tomto tématu uvádí některé běžné druh `for` smyčky, která umožňuje následující volby v částech:</span><span class="sxs-lookup"><span data-stu-id="d7878-146">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections:</span></span>
  
-   <span data-ttu-id="d7878-147">Inicializátoru deklaruje a inicializuje proměnnou místní smyčky `i`, který spravuje počet iterací smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-147">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="d7878-148">Podmínka kontroluje hodnotu proměnné smyčky proti známé konečná hodnota 5.</span><span class="sxs-lookup"><span data-stu-id="d7878-148">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="d7878-149">V části iterator používá výpisu operátory přírůstku `i++`, zaznamenávat každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="d7878-149">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>

## <a name="more-examples"></a><span data-ttu-id="d7878-150">Další příklady</span><span class="sxs-lookup"><span data-stu-id="d7878-150">More examples</span></span>
  
<span data-ttu-id="d7878-151">Následující příklad ilustruje několik méně běžné volby: přiřazení hodnoty proměnné externí smyčky v části inicializátoru, volání `Console.WriteLine` metoda v inicializátoru a iterator oddíly a změna hodnot dvě proměnné v části iterator.</span><span class="sxs-lookup"><span data-stu-id="d7878-151">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section, invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>
  
[!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
<span data-ttu-id="d7878-152">Všechny výrazy, které definují `for` příkaz jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="d7878-152">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="d7878-153">Například následující příkaz vytvoří nekonečná smyčka:</span><span class="sxs-lookup"><span data-stu-id="d7878-153">For example, the following statement creates an infinite loop:</span></span>
  
[!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d7878-154">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7878-154">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="d7878-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7878-155">See also</span></span>

[<span data-ttu-id="d7878-156">Pro příkaz (specifikace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d7878-156">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="d7878-157">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7878-157">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="d7878-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d7878-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="d7878-159">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7878-159">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="d7878-160">foreach, in</span><span class="sxs-lookup"><span data-stu-id="d7878-160">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
[<span data-ttu-id="d7878-161">for – příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="d7878-161">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="d7878-162">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="d7878-162">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
