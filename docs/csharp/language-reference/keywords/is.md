---
title: je - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306596"
---
# <a name="is-c-reference"></a><span data-ttu-id="9b951-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9b951-102">is (C# Reference)</span></span>

<span data-ttu-id="9b951-103">`is` Operátor zkontroluje, zda výsledek výrazu je kompatibilní s daným typem, nebo (počínaje C# 7.0) testuje výraz se vzorem.</span><span class="sxs-lookup"><span data-stu-id="9b951-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="9b951-104">Informace o typu testování `is` operátor viz [je operátor](../operators/type-testing-and-conversion-operators.md#is-operator) část [typové zkoušky a převod operátorů](../operators/type-testing-and-conversion-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="9b951-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-conversion-operators.md#is-operator) section of the [Type-testing and conversion operators](../operators/type-testing-and-conversion-operators.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="9b951-105">Porovnávání vzorů s `is`</span><span class="sxs-lookup"><span data-stu-id="9b951-105">Pattern matching with `is`</span></span>

<span data-ttu-id="9b951-106">Od verze C# 7.0, `is` a [přepnout](switch.md) příkazy podpory porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="9b951-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="9b951-107">`is` – Klíčové slovo podporuje následující způsoby:</span><span class="sxs-lookup"><span data-stu-id="9b951-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="9b951-108">[Typ vzorku](#type-pattern), který testuje, jestli výraz lze převést na zadaný typ a, pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="9b951-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="9b951-109">[Konstantní vzorek](#constant-pattern), který testuje, jestli je výraz vyhodnocen jako na zadanou hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="9b951-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="9b951-110">[vzor var](#var-pattern), shoda, který je vždy úspěšné a přiřazuje hodnotu výrazu nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="9b951-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="9b951-111">Vzorek typu</span><span class="sxs-lookup"><span data-stu-id="9b951-111">Type pattern</span></span>

<span data-ttu-id="9b951-112">Při použití typu modelu k provádění porovnávání vzorů, `is` testuje výraz lze převést na zadaný typ a pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="9b951-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="9b951-113">Je jednoduché rozšíření `is` příkaz, který umožňuje stručný typ vyhodnocení a převodu.</span><span class="sxs-lookup"><span data-stu-id="9b951-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="9b951-114">Obecný tvar `is` vzor typu je:</span><span class="sxs-lookup"><span data-stu-id="9b951-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="9b951-115">kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* se má převést a *název_proměnné* je objekt, na který výsledek *expr* je převedena, pokud `is` test je `true`.</span><span class="sxs-lookup"><span data-stu-id="9b951-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="9b951-116">`is` Výraz je `true` Pokud *expr* není `null`, a je splněna některá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="9b951-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="9b951-117">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="9b951-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="9b951-118">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="9b951-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="9b951-119">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="9b951-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="9b951-120">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="9b951-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="9b951-121">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="9b951-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="9b951-122">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="9b951-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="9b951-123">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b951-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="9b951-124">Počínaje C# 7.1, *expr* může mít za kompilace typu definované v parametru obecného typu a jeho omezení.</span><span class="sxs-lookup"><span data-stu-id="9b951-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="9b951-125">Pokud *expr* je `true` a `is` se používá s `if` příkazu *název_proměnné* přiřazují v rámci `if` pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b951-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="9b951-126">Rozsah *název_proměnné* z `is` výraz na konci uzavírající blok `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b951-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="9b951-127">Pomocí *název_proměnné* v jiném umístění vygeneruje chybu kompilace pro použití proměnné, která nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="9b951-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="9b951-128">V následujícím příkladu `is` vzor typu k dispozici implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9b951-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="9b951-129">Bez porovnávání vzorů, může být napsán takto následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9b951-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="9b951-130">Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null`.</span><span class="sxs-lookup"><span data-stu-id="9b951-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="9b951-131">`is` Vzor typu také vytvoří kompaktnějším kód při určování typu hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="9b951-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="9b951-132">V následujícím příkladu `is` vzor typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnota příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9b951-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="9b951-133">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, který obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="9b951-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="9b951-134">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="9b951-134">Constant pattern</span></span>

<span data-ttu-id="9b951-135">Při provádění porovnávání vzorů s konstantní vzorek `is` testuje, zda výraz rovná zadané – konstanta.</span><span class="sxs-lookup"><span data-stu-id="9b951-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="9b951-136">V jazyce C# 6 a starší verze, je podporován konstantní vzorek [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b951-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="9b951-137">Počínaje C# 7.0, je podporována `is` také příkaz.</span><span class="sxs-lookup"><span data-stu-id="9b951-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="9b951-138">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9b951-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="9b951-139">kde *expr* je výraz k vyhodnocení, a *konstantní* je hodnota pro testování.</span><span class="sxs-lookup"><span data-stu-id="9b951-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="9b951-140">*konstantní* může být následující konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="9b951-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="9b951-141">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="9b951-141">A literal value.</span></span>

- <span data-ttu-id="9b951-142">Název deklarovanou `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="9b951-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="9b951-143">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="9b951-143">An enumeration constant.</span></span>

<span data-ttu-id="9b951-144">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9b951-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="9b951-145">Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="9b951-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="9b951-146">V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="9b951-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="9b951-147">Následující příklad kombinuje typ a konstantní vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, k určení, zda dice kumulativní hodnotu 6.</span><span class="sxs-lookup"><span data-stu-id="9b951-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="9b951-148">Kontrola `null` je možné provádět pomocí konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="9b951-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="9b951-149">`null` – Klíčové slovo je podporován `is` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b951-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="9b951-150">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9b951-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="9b951-151">Následující příklad ukazuje porovnání `null` ověří:</span><span class="sxs-lookup"><span data-stu-id="9b951-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="9b951-152">vzor var</span><span class="sxs-lookup"><span data-stu-id="9b951-152">var pattern</span></span>

<span data-ttu-id="9b951-153">`var` Vzor je pokrývající vše pro libovolným typem nebo hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9b951-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="9b951-154">Hodnota *expr* se vždycky přiřazuje lokální proměnná stejný typ jako typ času kompilace *expr*.</span><span class="sxs-lookup"><span data-stu-id="9b951-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="9b951-155">Výsledkem `is` výraz je vždycky `true`.</span><span class="sxs-lookup"><span data-stu-id="9b951-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="9b951-156">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9b951-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="9b951-157">Následující příklad používá vzor var výrazu přiřazení k proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="9b951-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="9b951-158">Potom zobrazí hodnotu a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="9b951-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="9b951-159">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b951-159">C# language specification</span></span>
  
<span data-ttu-id="9b951-160">Další informace najdete v tématu [je operátor](~/_csharplang/spec/expressions.md#the-is-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md) a následující C# jazykové návrhy:</span><span class="sxs-lookup"><span data-stu-id="9b951-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="9b951-161">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="9b951-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="9b951-162">Porovnávání vzorů s obecnými typy</span><span class="sxs-lookup"><span data-stu-id="9b951-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="9b951-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b951-163">See also</span></span>

- [<span data-ttu-id="9b951-164">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="9b951-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9b951-165">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b951-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="9b951-166">Typové zkoušky a převod operátorů</span><span class="sxs-lookup"><span data-stu-id="9b951-166">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
