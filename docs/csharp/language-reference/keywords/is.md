---
title: is (Referenční dokumentace jazyka C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 8e4103f8e71858ec74c348ee1f675828e6468eb2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972165"
---
# <a name="is-c-reference"></a><span data-ttu-id="60169-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="60169-102">is (C# Reference)</span></span> #

<span data-ttu-id="60169-103">Zkontroluje, jestli je objekt kompatibilní s daným typem, nebo (od verze C# 7.0) testuje výraz se vzorem.</span><span class="sxs-lookup"><span data-stu-id="60169-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="60169-104">Testování kompatibility typu</span><span class="sxs-lookup"><span data-stu-id="60169-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="60169-105">`is` – Klíčové slovo vyhodnocen jako typ kompatibility za běhu.</span><span class="sxs-lookup"><span data-stu-id="60169-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="60169-106">Určuje, zda instance objektu nebo výsledek výrazu lze převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="60169-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="60169-107">Má syntaxi</span><span class="sxs-lookup"><span data-stu-id="60169-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="60169-108">kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* název typu, na který je výsledkem *expr* se má převést.</span><span class="sxs-lookup"><span data-stu-id="60169-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="60169-109">`is` Příkaz je `true` Pokud *expr* je null a objekt, který je výsledkem vyhodnocení výrazu může být převeden na *typ*; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="60169-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="60169-110">Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="60169-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="60169-111">`is` Příkaz má hodnotu true pokud:</span><span class="sxs-lookup"><span data-stu-id="60169-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="60169-112">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="60169-113">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="60169-114">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="60169-115">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="60169-116">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="60169-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="60169-117">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="60169-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="60169-118">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60169-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="60169-119">Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převodů.</span><span class="sxs-lookup"><span data-stu-id="60169-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="60169-120">`is` – Klíčové slovo vygeneruje upozornění kompilace, pokud je známo, že výraz vždy být buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="60169-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="60169-121">Uvažuje pouze převody odkazů, převodu zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="60169-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="60169-122">Následující příklad generuje upozornění, protože výsledkem převodu je známá v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="60169-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="60169-123">Všimněte si, že `is` výraz pro převod z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="60169-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="60169-124">`expr` může být libovolný výraz, který vrací hodnotu, s výjimkou anonymní metody a výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="60169-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="60169-125">Následující příklad používá `is` vyhodnotit vrácenou hodnotu volání metody.</span><span class="sxs-lookup"><span data-stu-id="60169-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="60169-126">Od verze C# 7.0, můžete použít porovnávání vzorů s [vzor typu](#type) zapsat stručnější kód, který používá `is` příkazu.</span><span class="sxs-lookup"><span data-stu-id="60169-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="60169-127">Porovnávání vzorů s `is`</span><span class="sxs-lookup"><span data-stu-id="60169-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="60169-128">Od verze C# 7.0, `is` a [přepnout](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="60169-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="60169-129">`is` – Klíčové slovo podporuje následující způsoby:</span><span class="sxs-lookup"><span data-stu-id="60169-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="60169-130">[Typ vzorku](#type), který testuje, jestli výraz lze převést na zadaný typ a, pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="60169-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="60169-131">[Konstantní vzorek](#constant), který testuje, jestli je výraz vyhodnocen jako na zadanou hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="60169-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="60169-132">[vzor var](#var), shoda, který je vždy úspěšné a přiřazuje hodnotu výrazu nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="60169-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="60169-133"><a name="type" /> Vzorek typu </a></span><span class="sxs-lookup"><span data-stu-id="60169-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="60169-134">Při použití typu modelu k provádění porovnávání vzorů, `is` testuje výraz lze převést na zadaný typ a pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="60169-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="60169-135">Je jednoduché rozšíření `is` příkaz, který umožňuje stručný typ vyhodnocení a převodu.</span><span class="sxs-lookup"><span data-stu-id="60169-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="60169-136">Obecný tvar `is` vzor typu je:</span><span class="sxs-lookup"><span data-stu-id="60169-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="60169-137">kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* se má převést a *název_proměnné* je objekt, na který výsledek *expr* je převedena, pokud `is` test je `true`.</span><span class="sxs-lookup"><span data-stu-id="60169-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="60169-138">`is` Výraz je `true` Pokud *expr* není `null`, a je splněna některá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="60169-138">The `is` expression is `true` if *expr* is not `null`, and any of the following is true:</span></span>

- <span data-ttu-id="60169-139">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="60169-140">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="60169-141">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="60169-142">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="60169-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="60169-143">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="60169-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="60169-144">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="60169-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="60169-145">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60169-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="60169-146">Pokud *expr* je `true` a `is` se používá s `if` příkazu *název_proměnné* přiřazena a místním rozsahem v rámci `if` pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="60169-146">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="60169-147">V následujícím příkladu `is` vzor typu k dispozici implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="60169-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="60169-148">Bez porovnávání vzorů, může být napsán takto následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="60169-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="60169-149">Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null`.</span><span class="sxs-lookup"><span data-stu-id="60169-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="60169-150">`is` Vzor typu také vytvoří kompaktnějším kód při určování typu hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="60169-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="60169-151">V následujícím příkladu `is` vzor typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnota příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="60169-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="60169-152">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, který obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="60169-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="60169-153"><a name="constant" /> Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="60169-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="60169-154">Při provádění porovnávání vzorů s konstantní vzorek `is` testuje, zda výraz rovná zadané – konstanta.</span><span class="sxs-lookup"><span data-stu-id="60169-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="60169-155">V jazyce C# 6 a starší verze, je podporován konstantní vzorek [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="60169-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="60169-156">Od verze C# 7.0, je podporována `is` také příkaz.</span><span class="sxs-lookup"><span data-stu-id="60169-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="60169-157">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="60169-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="60169-158">kde *expr* je výraz k vyhodnocení, a *konstantní* je hodnota pro testování.</span><span class="sxs-lookup"><span data-stu-id="60169-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="60169-159">*konstantní* může být následující konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="60169-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="60169-160">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="60169-160">A literal value.</span></span>

- <span data-ttu-id="60169-161">Název deklarovanou `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="60169-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="60169-162">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="60169-162">An enumeration constant.</span></span>

<span data-ttu-id="60169-163">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="60169-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="60169-164">Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="60169-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="60169-165">V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="60169-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="60169-166">Následující příklad kombinuje typ a konstantní vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, k určení, zda dice kumulativní hodnotu 6.</span><span class="sxs-lookup"><span data-stu-id="60169-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="60169-167">Kontrola `null` je možné provádět pomocí konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="60169-167">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="60169-168">`null` – Klíčové slovo je podporován `is` příkazu.</span><span class="sxs-lookup"><span data-stu-id="60169-168">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="60169-169">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="60169-169">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="60169-170">Následující příklad ukazuje porovnání `null` ověří:</span><span class="sxs-lookup"><span data-stu-id="60169-170">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="60169-171"><a name="var" /> vzor var </a></span><span class="sxs-lookup"><span data-stu-id="60169-171"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="60169-172">Porovnávání se vzorem var vždy úspěšná.</span><span class="sxs-lookup"><span data-stu-id="60169-172">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="60169-173">Syntaxe je</span><span class="sxs-lookup"><span data-stu-id="60169-173">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="60169-174">Pokud hodnota *expr* se vždycky přiřazuje na místní proměnnou s názvem *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="60169-174">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="60169-175">*název_proměnné* je statická proměnná stejného typu jako *expr*.</span><span class="sxs-lookup"><span data-stu-id="60169-175">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="60169-176">Následující příklad používá vzor var výrazu přiřazení k proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="60169-176">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="60169-177">Potom zobrazí hodnotu a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="60169-177">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="60169-178">Všimněte si, že pokud *expr* je `null`, `is` výrazu stále platí a přiřadí `null` k *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="60169-178">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="60169-179">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60169-179">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60169-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60169-180">See also</span></span>

- [<span data-ttu-id="60169-181">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60169-181">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="60169-182">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60169-182">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="60169-183">typeof</span><span class="sxs-lookup"><span data-stu-id="60169-183">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
- [<span data-ttu-id="60169-184">as</span><span class="sxs-lookup"><span data-stu-id="60169-184">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
- [<span data-ttu-id="60169-185">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="60169-185">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
