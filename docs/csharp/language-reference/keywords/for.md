---
title: "for (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="7eb62-102">for (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7eb62-102">for (C# Reference)</span></span>
<span data-ttu-id="7eb62-103">Pomocí `for` smyčku, můžete spustit příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`.</span><span class="sxs-lookup"><span data-stu-id="7eb62-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="7eb62-104">Tento druh smyčky je užitečný pro iterování přes pole a pro jiné aplikace, ve kterých víte předem kolikrát chcete, aby k iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eb62-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7eb62-105">Example</span></span>  
 <span data-ttu-id="7eb62-106">V následujícím příkladu, hodnota `i` je zapsána do konzoly a zvýší o 1 při každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="7eb62-107">`for` Příkaz v předchozím příkladu provede následující akce.</span><span class="sxs-lookup"><span data-stu-id="7eb62-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="7eb62-108">První, počáteční hodnota proměnné `i` je vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="7eb62-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="7eb62-109">Tento krok se stane pouze jednou, bez ohledu na to, jak mnohokrát opakuje smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="7eb62-110">Tato inicializace si můžete představit jako situaci mimo proces opakování.</span><span class="sxs-lookup"><span data-stu-id="7eb62-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="7eb62-111">Při vyhodnocení podmínky (`i <= 5`), hodnota `i` se porovná s 5.</span><span class="sxs-lookup"><span data-stu-id="7eb62-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="7eb62-112">Pokud `i` je menší než nebo rovna 5, je podmínka vyhodnocena jako `true`, a dojde k následujícím akcím.</span><span class="sxs-lookup"><span data-stu-id="7eb62-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="7eb62-113">`Console.WriteLine` Příkaz do těla smyčky zobrazuje hodnotu `i`.</span><span class="sxs-lookup"><span data-stu-id="7eb62-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="7eb62-114">Hodnota `i` se zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="7eb62-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="7eb62-115">Smyčky vrátí začátek krok 2: vyhodnocení podmínky znovu.</span><span class="sxs-lookup"><span data-stu-id="7eb62-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="7eb62-116">Pokud `i` je větší než 5, je podmínka vyhodnocena jako `false`, a ukončení smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="7eb62-117">Všimněte si, že, pokud počáteční hodnota `i` je větší než 5, do těla smyčky nefunguje i jednou.</span><span class="sxs-lookup"><span data-stu-id="7eb62-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="7eb62-118">Každý `for` příkaz definuje inicializátoru, podmínku a iterator oddíly.</span><span class="sxs-lookup"><span data-stu-id="7eb62-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="7eb62-119">Tyto části obvykle určit počet opakování iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="7eb62-120">V částech slouží k následujícím účelům.</span><span class="sxs-lookup"><span data-stu-id="7eb62-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="7eb62-121">V části inicializátoru nastaví počáteční podmínky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="7eb62-122">Příkazy v této části spustit jenom jednou před zadáním smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="7eb62-123">V části může obsahovat pouze jednu z následujících dvou možností.</span><span class="sxs-lookup"><span data-stu-id="7eb62-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="7eb62-124">Deklarace a inicializace proměnné místní smyčky, jak ukazuje příklad první (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="7eb62-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="7eb62-125">Proměnná je místní pro smyčky a není přístupný z mimo smyčku.</span><span class="sxs-lookup"><span data-stu-id="7eb62-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="7eb62-126">Nula nebo více příkaz expressons z následujícího seznamu, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="7eb62-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="7eb62-127">[přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="7eb62-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="7eb62-128">volání metody</span><span class="sxs-lookup"><span data-stu-id="7eb62-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="7eb62-129">předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="7eb62-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="7eb62-130">předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="7eb62-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="7eb62-131">Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7eb62-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="7eb62-132">[await](../../../csharp/language-reference/keywords/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="7eb62-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="7eb62-133">Podmínka oddíl obsahuje logický výraz, který se vyhodnotí k určení, zda smyčky musí ukončit nebo měli znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="7eb62-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="7eb62-134">Iterator oddíl definuje, co se stane po každé iteraci těla smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="7eb62-135">Iterator obsahuje nula nebo více z těchto výrazů příkaz oddělené čárkami:</span><span class="sxs-lookup"><span data-stu-id="7eb62-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="7eb62-136">[přiřazení](../../../csharp/language-reference/operators/assignment-operator.md) – příkaz</span><span class="sxs-lookup"><span data-stu-id="7eb62-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="7eb62-137">volání metody</span><span class="sxs-lookup"><span data-stu-id="7eb62-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="7eb62-138">předpony nebo přípony [přírůstek](../../../csharp/language-reference/operators/increment-operator.md) výrazu, jako například `++i` nebo`i++`</span><span class="sxs-lookup"><span data-stu-id="7eb62-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="7eb62-139">předpony nebo přípony [snížení](../../../csharp/language-reference/operators/decrement-operator.md) výrazu, jako například `--i` nebo`i--`</span><span class="sxs-lookup"><span data-stu-id="7eb62-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="7eb62-140">Vytvoření objektu pomocí [nové](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7eb62-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="7eb62-141">[await](../../../csharp/language-reference/keywords/await.md) výraz</span><span class="sxs-lookup"><span data-stu-id="7eb62-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="7eb62-142">Do těla smyčky se skládá z příkazu, prázdný příkaz nebo blok příkazů, které vytvoříte uzavřením nula nebo více příkazů do složených závorek.</span><span class="sxs-lookup"><span data-stu-id="7eb62-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="7eb62-143">Můžete rozdělit mimo `for` smyčky pomocí [zalomení](../../../csharp/language-reference/keywords/break.md) – klíčové slovo, nebo můžete do další iterace krok pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7eb62-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="7eb62-144">Také můžete ukončit všechny smyčky pomocí [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="7eb62-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="7eb62-145">V prvním příkladu v tomto tématu uvádí některé běžné druh `for` smyčky, která umožňuje následující volby v částech.</span><span class="sxs-lookup"><span data-stu-id="7eb62-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="7eb62-146">Inicializátoru deklaruje a inicializuje proměnnou místní smyčky `i`, který spravuje počet iterací smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="7eb62-147">Podmínka kontroluje hodnotu proměnné smyčky proti známé konečná hodnota 5.</span><span class="sxs-lookup"><span data-stu-id="7eb62-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="7eb62-148">V části iterator používá výpisu operátory přírůstku `i++`, zaznamenávat každé iteraci smyčky.</span><span class="sxs-lookup"><span data-stu-id="7eb62-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="7eb62-149">Následující příklad ilustruje několik méně běžné volby: přiřazení hodnoty proměnné externí smyčky v části inicializátoru, volání `Console.WriteLine` metoda v inicializátoru a iterator oddíly a změna hodnot dvě proměnné v části iterator.</span><span class="sxs-lookup"><span data-stu-id="7eb62-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="7eb62-150">Všechny výrazy, které definují `for` příkaz jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="7eb62-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="7eb62-151">Například následující příkaz vytvoří nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="7eb62-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7eb62-152">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7eb62-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7eb62-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="7eb62-153">See Also</span></span>  
 [<span data-ttu-id="7eb62-154">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7eb62-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7eb62-155">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="7eb62-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7eb62-156">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7eb62-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7eb62-157">foreach v</span><span class="sxs-lookup"><span data-stu-id="7eb62-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="7eb62-158">pro příkaz (C++)</span><span class="sxs-lookup"><span data-stu-id="7eb62-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="7eb62-159">Příkazy iterace</span><span class="sxs-lookup"><span data-stu-id="7eb62-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
