---
description: is-reference jazyka C#
title: is-reference jazyka C#
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 3508f08857f88fd34478f968a71bae0121d54d1c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134507"
---
# <a name="is-c-reference"></a><span data-ttu-id="9c6ac-103">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9c6ac-103">is (C# Reference)</span></span>

<span data-ttu-id="9c6ac-104">`is`Operátor zkontroluje, zda je výsledek výrazu kompatibilní s daným typem, nebo (počínaje jazykem C# 7,0) testuje výraz na vzor.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-104">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="9c6ac-105">Informace o `is` operátoru testování typu najdete v části [operátor is](../operators/type-testing-and-cast.md#is-operator) pro [operátory typu testování a přetypování](../operators/type-testing-and-cast.md) .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-105">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="9c6ac-106">Porovnávání vzorů s `is`</span><span class="sxs-lookup"><span data-stu-id="9c6ac-106">Pattern matching with `is`</span></span>

<span data-ttu-id="9c6ac-107">Počínaje jazykem C# 7,0 `is` příkazy a [přepínače](switch.md) podporují porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-107">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="9c6ac-108">`is`Klíčové slovo podporuje následující vzory:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-108">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="9c6ac-109">[Vzor typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování jej na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-109">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="9c6ac-110">[Konstantní vzor](#constant-pattern), který testuje, zda je výraz vyhodnocen na zadanou konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-110">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="9c6ac-111">[var Pattern](#var-pattern), porovnávání, které vždy uspěje a váže hodnotu výrazu k nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-111">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="9c6ac-112">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="9c6ac-112">Type pattern</span></span>

<span data-ttu-id="9c6ac-113">Při použití vzoru typu pro porovnávání vzorů testuje, `is` zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-113">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="9c6ac-114">Je to jasné rozšíření `is` příkazu, které umožňuje vyhodnocování a konverzi stručných typů.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-114">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="9c6ac-115">Obecná forma `is` vzoru typu je:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-115">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="9c6ac-116">Kde *výraz* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud `is` je test `true` .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-116">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="9c6ac-117">`is`Výraz je `true` if není *expr* `null` a kterákoli z následujících možností je true:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-117">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="9c6ac-118">*výraz* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-118">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="9c6ac-119">*expr* je instance typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-119">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="9c6ac-120">Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-120">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="9c6ac-121">*výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-121">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="9c6ac-122">*Typ v čase kompilace* proměnné je typ proměnné definovaný v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-122">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="9c6ac-123">*Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-123">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="9c6ac-124">*expr* je instance typu, který implementuje rozhraní *typu* .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-124">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="9c6ac-125">Počínaje jazykem C# 7,1, *expr* může být typ kompilace definovaný parametrem obecného typu a jeho omezeními.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-125">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="9c6ac-126">Je-li *výraz expr* `true` a `is` je použit s `if` příkazem *varname* , je přiřazena pouze v rámci `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-126">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="9c6ac-127">Rozsah *název_proměnné* je z `is` výrazu na konec bloku ohraničujícího `if` příkaz.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-127">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="9c6ac-128">Použití *název_proměnné* v jakémkoli jiném umístění generuje chybu při kompilaci pro použití proměnné, která nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-128">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="9c6ac-129">Následující příklad používá `is` vzor typu k poskytnutí implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-129">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="9c6ac-130">Bez porovnávání vzorů může být tento kód napsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-130">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="9c6ac-131">Použití porovnávání vzorů typů vytváří více kompaktních a čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-131">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="9c6ac-132">`is`Vzor typu také při určování typu hodnoty vytvoří více kompaktního kódu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-132">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="9c6ac-133">V následujícím příkladu je použit `is` vzorek typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnoty příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-133">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="9c6ac-134">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-134">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="9c6ac-135">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="9c6ac-135">Constant pattern</span></span>

<span data-ttu-id="9c6ac-136">Při provádění porovnávání vzorů s konstantním vzorem `is` otestuje, zda výraz odpovídá zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-136">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="9c6ac-137">V jazyce C# 6 a starších verzích je konstantní vzorek podporován příkazem [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-137">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="9c6ac-138">Počínaje jazykem C# 7,0 je podporováno `is` také příkazem.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-138">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="9c6ac-139">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-139">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="9c6ac-140">kde *expr* je výraz, který se má vyhodnotit, a *konstanta* je hodnota, která se má testovat.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-140">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="9c6ac-141">*konstanta* může být libovolný z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-141">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="9c6ac-142">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-142">A literal value.</span></span>

- <span data-ttu-id="9c6ac-143">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-143">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="9c6ac-144">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-144">An enumeration constant.</span></span>

<span data-ttu-id="9c6ac-145">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-145">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="9c6ac-146">Pokud je *výraz* a *konstanta* integrální typy, operátor rovnosti jazyka C# určuje, zda výraz vrátí hodnotu `true` (tj `expr == constant` . zda).</span><span class="sxs-lookup"><span data-stu-id="9c6ac-146">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="9c6ac-147">V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="9c6ac-147">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="9c6ac-148">Následující příklad kombinuje vzorce typu a konstanty k otestování, zda je objekt `Dice` instancí, a pokud je, k určení, zda je hodnota indexu předána 6.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-148">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="9c6ac-149">Kontrolu `null` lze provést pomocí konstantního vzoru.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-149">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="9c6ac-150">`null`Klíčové slovo je podporováno `is` příkazem.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-150">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="9c6ac-151">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-151">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="9c6ac-152">Následující příklad ukazuje porovnání `null` kontrol:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-152">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="9c6ac-153">variabilní vzorek</span><span class="sxs-lookup"><span data-stu-id="9c6ac-153">var pattern</span></span>

<span data-ttu-id="9c6ac-154">Vzor porovnávání se `var` vzorem vždy proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-154">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="9c6ac-155">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-155">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="9c6ac-156">Kde hodnota *expr* je vždy přiřazena místní proměnné s názvem *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-156">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="9c6ac-157">*název_proměnné* je proměnná stejného typu jako typ *výrazu*při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-157">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="9c6ac-158">Pokud je *výraz* vyhodnocen jako `null` , `is` výraz vytvoří `true` a přiřadí `null` k *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-158">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="9c6ac-159">Vzor var je jedno z několika použití `is` , které vytváří `true` `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-159">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="9c6ac-160">Pomocí `var` vzoru můžete vytvořit dočasnou proměnnou v rámci logického výrazu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-160">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="9c6ac-161">V předchozím příkladu se dočasná proměnná používá k uložení výsledku nákladné operace.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-161">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="9c6ac-162">Proměnnou je pak možné použít několikrát.</span><span class="sxs-lookup"><span data-stu-id="9c6ac-162">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9c6ac-163">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c6ac-163">C# language specification</span></span>
  
<span data-ttu-id="9c6ac-164">Další informace naleznete v části [operátor is](~/_csharplang/spec/expressions.md#the-is-operator) v tématu [specifikace jazyka c#](~/_csharplang/spec/introduction.md) a v následujících návrzích jazyka c#:</span><span class="sxs-lookup"><span data-stu-id="9c6ac-164">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="9c6ac-165">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="9c6ac-165">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="9c6ac-166">Porovnávání vzorů s obecnými typy</span><span class="sxs-lookup"><span data-stu-id="9c6ac-166">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="9c6ac-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c6ac-167">See also</span></span>

- [<span data-ttu-id="9c6ac-168">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="9c6ac-168">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9c6ac-169">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c6ac-169">C# keywords</span></span>](index.md)
- [<span data-ttu-id="9c6ac-170">Operátory pro testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="9c6ac-170">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
