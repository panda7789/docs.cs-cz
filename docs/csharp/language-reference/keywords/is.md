---
title: je C# odkaz
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 1a1f539e80f8d843f40640fa798cf6122f316a9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715240"
---
# <a name="is-c-reference"></a><span data-ttu-id="bd317-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bd317-102">is (C# Reference)</span></span>

<span data-ttu-id="bd317-103">Operátor `is` kontroluje, zda je výsledek výrazu kompatibilní s daným typem nebo (počínaje C# 7,0) testuje výraz na vzor.</span><span class="sxs-lookup"><span data-stu-id="bd317-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="bd317-104">Informace o operátoru `is` testování typu naleznete v článku [operátor is](../operators/type-testing-and-cast.md#is-operator) pro [operátory typu testování a přetypování](../operators/type-testing-and-cast.md) .</span><span class="sxs-lookup"><span data-stu-id="bd317-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="bd317-105">Porovnávání vzorů s `is`</span><span class="sxs-lookup"><span data-stu-id="bd317-105">Pattern matching with `is`</span></span>

<span data-ttu-id="bd317-106">Počínaje C# 7,0, příkazy `is` a [Switch](switch.md) podporují porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="bd317-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="bd317-107">Klíčové slovo `is` podporuje následující vzory:</span><span class="sxs-lookup"><span data-stu-id="bd317-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="bd317-108">[Vzor typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování jej na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="bd317-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="bd317-109">[Konstantní vzor](#constant-pattern), který testuje, zda je výraz vyhodnocen na zadanou konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bd317-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="bd317-110">[var Pattern](#var-pattern), porovnávání, které vždy uspěje a váže hodnotu výrazu k nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd317-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="bd317-111">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="bd317-111">Type pattern</span></span>

<span data-ttu-id="bd317-112">Při použití vzoru typu k provedení porovnávání se vzorem `is` testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="bd317-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="bd317-113">Je to jasné rozšíření příkazu `is`, které umožňuje vyhodnocování a konverzi stručných typů.</span><span class="sxs-lookup"><span data-stu-id="bd317-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="bd317-114">Obecná forma `is`ho vzoru typu je:</span><span class="sxs-lookup"><span data-stu-id="bd317-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="bd317-115">kde *expr* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je `is` test `true`.</span><span class="sxs-lookup"><span data-stu-id="bd317-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="bd317-116">Výraz `is` je `true`, pokud *výraz* není `null`a kterákoli z následujících možností je pravdivá:</span><span class="sxs-lookup"><span data-stu-id="bd317-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="bd317-117">*výraz* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="bd317-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="bd317-118">*expr* je instance typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd317-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="bd317-119">Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd317-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="bd317-120">*výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*.</span><span class="sxs-lookup"><span data-stu-id="bd317-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="bd317-121">*Typ v čase kompilace* proměnné je typ proměnné definovaný v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="bd317-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="bd317-122">*Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd317-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="bd317-123">*expr* je instance typu, který implementuje rozhraní *typu* .</span><span class="sxs-lookup"><span data-stu-id="bd317-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="bd317-124">Počínaje C# 7,1, *expr* může být typ kompilace definovaný parametrem obecného typu a jeho omezeními.</span><span class="sxs-lookup"><span data-stu-id="bd317-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="bd317-125">Je-li *výraz expr* `true` a je-li `is` použit s příkazem `if`, je příkaz *název_proměnné* přiřazen pouze v rámci příkazu `if`.</span><span class="sxs-lookup"><span data-stu-id="bd317-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="bd317-126">Rozsah *název_proměnné* je z výrazu `is` na konec bloku ohraničujícího příkaz `if`.</span><span class="sxs-lookup"><span data-stu-id="bd317-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="bd317-127">Použití *název_proměnné* v jakémkoli jiném umístění generuje chybu při kompilaci pro použití proměnné, která nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="bd317-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="bd317-128">Následující příklad používá vzor typu `is` k poskytnutí implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.</span><span class="sxs-lookup"><span data-stu-id="bd317-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="bd317-129">Bez porovnávání vzorů může být tento kód napsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bd317-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="bd317-130">Použití porovnávání vzorů typů vytváří více kompaktních čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null`.</span><span class="sxs-lookup"><span data-stu-id="bd317-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="bd317-131">Vzor typu `is` také při určování typu hodnoty vytvoří více kompaktního kódu.</span><span class="sxs-lookup"><span data-stu-id="bd317-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="bd317-132">V následujícím příkladu je použit vzor typu `is` k určení, zda je objekt `Person` nebo instance `Dog` před zobrazením hodnoty příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bd317-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="bd317-133">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="bd317-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="bd317-134">Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="bd317-134">Constant pattern</span></span>

<span data-ttu-id="bd317-135">Při provádění porovnávání vzorů s konstantním vzorem `is` testuje, zda výraz odpovídá zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="bd317-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="bd317-136">V C# 6 a starších verzích je konstantní vzorek podporován příkazem [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="bd317-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="bd317-137">Počínaje C# 7,0 se podporuje i příkaz `is`.</span><span class="sxs-lookup"><span data-stu-id="bd317-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="bd317-138">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="bd317-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="bd317-139">kde *expr* je výraz, který se má vyhodnotit, a *konstanta* je hodnota, která se má testovat.</span><span class="sxs-lookup"><span data-stu-id="bd317-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="bd317-140">*konstanta* může být libovolný z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="bd317-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="bd317-141">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="bd317-141">A literal value.</span></span>

- <span data-ttu-id="bd317-142">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="bd317-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="bd317-143">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="bd317-143">An enumeration constant.</span></span>

<span data-ttu-id="bd317-144">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bd317-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="bd317-145">Je *-li výraz* a *konstanta* integrální typy C# , operátor rovnosti určuje, zda výraz vrátí hodnotu `true` (tj. zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="bd317-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="bd317-146">V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="bd317-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="bd317-147">Následující příklad kombinuje vzorce typu a konstanty k otestování, zda je objekt `Dice` instance a, pokud je, k určení, zda je hodnota indexu vrácena 6.</span><span class="sxs-lookup"><span data-stu-id="bd317-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="bd317-148">Kontrolu `null` lze provést pomocí konstantního vzoru.</span><span class="sxs-lookup"><span data-stu-id="bd317-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="bd317-149">Klíčové slovo `null` je podporováno příkazem `is`.</span><span class="sxs-lookup"><span data-stu-id="bd317-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="bd317-150">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="bd317-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="bd317-151">Následující příklad ukazuje porovnání `null` kontroly:</span><span class="sxs-lookup"><span data-stu-id="bd317-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="bd317-152">variabilní vzorek</span><span class="sxs-lookup"><span data-stu-id="bd317-152">var pattern</span></span>

<span data-ttu-id="bd317-153">Vzor `var` je catch-All pro libovolný typ nebo hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bd317-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="bd317-154">Hodnota *expr* je vždy přiřazena místní proměnné, která má stejný typ jako typ času kompilace *expr*.</span><span class="sxs-lookup"><span data-stu-id="bd317-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="bd317-155">Výsledek výrazu `is` je vždy `true`.</span><span class="sxs-lookup"><span data-stu-id="bd317-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="bd317-156">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="bd317-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="bd317-157">V následujícím příkladu je použit vzorek var pro přiřazení výrazu proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="bd317-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="bd317-158">Pak zobrazí hodnotu a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="bd317-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="bd317-159">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd317-159">C# language specification</span></span>
  
<span data-ttu-id="bd317-160">Další informace najdete v části [operátor is](~/_csharplang/spec/expressions.md#the-is-operator) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md) a v následujících C# jazykových návrzích:</span><span class="sxs-lookup"><span data-stu-id="bd317-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="bd317-161">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="bd317-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="bd317-162">Porovnávání vzorů s obecnými typy</span><span class="sxs-lookup"><span data-stu-id="bd317-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="bd317-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd317-163">See also</span></span>

- [<span data-ttu-id="bd317-164">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="bd317-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bd317-165">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bd317-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="bd317-166">Operátory testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="bd317-166">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
