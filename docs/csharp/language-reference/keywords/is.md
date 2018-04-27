---
title: is (Referenční dokumentace jazyka C#)
keywords: je klíčové slovo (C#), je (C#)
ms.date: 02/17/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44c15eb9d65adf10904f8777847b0653ff1dbc99
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="is-c-reference"></a><span data-ttu-id="1e310-103">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1e310-103">is (C# Reference)</span></span> #

<span data-ttu-id="1e310-104">Zkontroluje, jestli je objekt kompatibilní s daného typu, nebo (C# 7.0 počínaje) testy výraz se vzorem.</span><span class="sxs-lookup"><span data-stu-id="1e310-104">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="1e310-105">Testování kompatibility typu</span><span class="sxs-lookup"><span data-stu-id="1e310-105">Testing for type compatibility</span></span> ##

<span data-ttu-id="1e310-106">`is` – Klíčové slovo vyhodnotí kompatibility typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="1e310-106">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="1e310-107">Určuje, zda instanci objektu nebo výsledek výrazu lze převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="1e310-107">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="1e310-108">Má syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e310-108">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="1e310-109">kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* je název typu, na který výsledek *expr* chcete převést.</span><span class="sxs-lookup"><span data-stu-id="1e310-109">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="1e310-110">`is` Příkaz je `true` Pokud *expr* jinou hodnotu než null a objekt, který výsledků vyhodnocení výrazu může být převeden na *typ*, jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="1e310-110">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="1e310-111">Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="1e310-111">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="1e310-112">`is` Příkaz je hodnota true, pokud:</span><span class="sxs-lookup"><span data-stu-id="1e310-112">The `is` statement is true if:</span></span>

- <span data-ttu-id="1e310-113">*Expr* je instance stejného typu jako *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-113">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1e310-114">*Expr* představuje instanci typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-114">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1e310-115">Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-115">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1e310-116">*Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-116">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1e310-117">*Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="1e310-117">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="1e310-118">*Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="1e310-118">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1e310-119">*Expr* představuje instanci typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e310-119">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1e310-120">Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převody.</span><span class="sxs-lookup"><span data-stu-id="1e310-120">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="1e310-121">`is` – Klíčové slovo vygeneruje kompilaci upozornění, pokud je znám výraz vždycky být buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="1e310-121">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="1e310-122">Uvažuje pouze převody odkazů, převodů zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="1e310-122">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="1e310-123">V následujícím příkladu generuje upozornění, protože je v době kompilace výsledek převodu.</span><span class="sxs-lookup"><span data-stu-id="1e310-123">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="1e310-124">Všimněte si, že `is` výraz převody z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="1e310-124">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="1e310-125">`expr` může být jakékoli výraz, který vrátí hodnotu, s výjimkou anonymní metody a výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="1e310-125">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="1e310-126">Následující příklad používá `is` vyhodnotit návratovou hodnotu volání metody.</span><span class="sxs-lookup"><span data-stu-id="1e310-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="1e310-127">Od verze 7.0 C#, můžete použít porovnávání vzorů s [typ vzor](#type) napsat přesnější kód, který používá `is` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1e310-127">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="1e310-128">Pro porovnávání s `is`</span><span class="sxs-lookup"><span data-stu-id="1e310-128">Pattern matching with `is`</span></span> ##

<span data-ttu-id="1e310-129">Od verze jazyka C# 7.0, `is` a [přepínače](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="1e310-129">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="1e310-130">`is` – Klíčové slovo podporuje následující vzorce:</span><span class="sxs-lookup"><span data-stu-id="1e310-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="1e310-131">[Typ vzor](#type), který kontroluje, zda výraz lze převést na zadaný typ a, pokud lze, obsahuje ji proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="1e310-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="1e310-132">[Konstantní vzor](#constant), který kontroluje, zda výsledkem konstantní hodnotu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="1e310-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="1e310-133">[var – vzor](#var), shoda, který vždy úspěšné a sváže hodnotu výrazu nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="1e310-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="1e310-134"><a name="type" /> Typ vzor </a></span><span class="sxs-lookup"><span data-stu-id="1e310-134"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="1e310-135">Při provádění porovnávání vzorů pomocí vzoru typ `is` testuje, zda výraz lze převést na zadaný typ a pokud jej lze obsahuje ji proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="1e310-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="1e310-136">Je přehledné rozšíření `is` příkaz, který umožňuje stručným typ vyhodnocení a převod.</span><span class="sxs-lookup"><span data-stu-id="1e310-136">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="1e310-137">Obecná forma `is` typ vzor je:</span><span class="sxs-lookup"><span data-stu-id="1e310-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="1e310-138">kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* chcete převést a *název_proměnné* je objekt, ke kterému výsledek *expr* je převést, pokud `is` test je `true`.</span><span class="sxs-lookup"><span data-stu-id="1e310-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="1e310-139">`is` Výraz `true` Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="1e310-139">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="1e310-140">*Expr* je instance stejného typu jako *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1e310-141">*Expr* představuje instanci typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1e310-142">Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1e310-143">*Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu*.</span><span class="sxs-lookup"><span data-stu-id="1e310-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1e310-144">*Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="1e310-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="1e310-145">*Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="1e310-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1e310-146">*Expr* představuje instanci typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1e310-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1e310-147">Pokud *exp* je `true` a `is` se používá s `if` příkaz *název_proměnné* je přiřazen a má místní rozsah v rámci `if` pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="1e310-147">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="1e310-148">Následující příklad používá `is` typ vzor k zajištění implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1e310-148">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="1e310-149">Bez porovnávání vzorů, může tento kód zapsat takto.</span><span class="sxs-lookup"><span data-stu-id="1e310-149">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="1e310-150">Použití porovnávání vzorů typu vytváří odstraněním potřeba otestovat, zda je výsledek převodu z kódu kompaktnější a čitelné `null`.</span><span class="sxs-lookup"><span data-stu-id="1e310-150">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="1e310-151">`is` Typ vzor také vytváří kompaktnější kód při určování typ typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1e310-151">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="1e310-152">Následující příklad používá `is` typ vzor k určení, zda je objekt `Person` nebo `Dog` instance, než se zobrazí hodnota příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e310-152">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="1e310-153">Kód ekvivalentní bez odpovídající vzor vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="1e310-153">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="1e310-154"><a name="constant" /> Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="1e310-154"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="1e310-155">Při provádění porovnávání s konstantní vzor vzorů `is` testuje, zda výraz rovná zadané konstanta.</span><span class="sxs-lookup"><span data-stu-id="1e310-155">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="1e310-156">V jazyce C# 6 a starší verze, konstantní vzor podporuje [přepínač](switch.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="1e310-156">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="1e310-157">Od verze 7.0 C#, je podporována `is` příkaz také.</span><span class="sxs-lookup"><span data-stu-id="1e310-157">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="1e310-158">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="1e310-158">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="1e310-159">kde *expr* se výraz, který chcete vyhodnotit, a *konstantní* je hodnota, kterou chcete otestovat.</span><span class="sxs-lookup"><span data-stu-id="1e310-159">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="1e310-160">*konstantní* může být libovolná z následujících konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="1e310-160">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="1e310-161">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="1e310-161">A literal value.</span></span>

- <span data-ttu-id="1e310-162">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="1e310-162">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="1e310-163">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="1e310-163">An enumeration constant.</span></span>

<span data-ttu-id="1e310-164">Konstantní výraz je vyhodnotit takto:</span><span class="sxs-lookup"><span data-stu-id="1e310-164">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="1e310-165">Pokud *expr* a *konstantní* jsou integrální typy operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="1e310-165">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="1e310-166">Jinak hodnota výrazu je určena voláním statických [Object.Equals (výraz, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metoda.</span><span class="sxs-lookup"><span data-stu-id="1e310-166">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="1e310-167">Následující příklad kombinuje typu a konstanta vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, chcete-li zjistit jestli rozčlenění kumulativní hodnotu 6.</span><span class="sxs-lookup"><span data-stu-id="1e310-167">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="1e310-168"><a name="var" /> var – vzor </a></span><span class="sxs-lookup"><span data-stu-id="1e310-168"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="1e310-169">Vzor shody s var vzor je vždy úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1e310-169">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="1e310-170">Jeho syntaxe je</span><span class="sxs-lookup"><span data-stu-id="1e310-170">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="1e310-171">kde hodnota *expr* se vždycky přiřazuje místní proměnné s názvem *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="1e310-171">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="1e310-172">*název_proměnné* je statická proměnná stejného typu jako *expr*.</span><span class="sxs-lookup"><span data-stu-id="1e310-172">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="1e310-173">Následující příklad používá var vzor výrazu přiřadit proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="1e310-173">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="1e310-174">Potom zobrazí hodnota a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="1e310-174">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="1e310-175">Všimněte si, že pokud *expr* je `null`, `is` výraz stále platí a přiřadí `null` k *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="1e310-175">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="1e310-176">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1e310-176">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1e310-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e310-177">See also</span></span>  
 [<span data-ttu-id="1e310-178">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1e310-178">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1e310-179">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1e310-179">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1e310-180">typeof</span><span class="sxs-lookup"><span data-stu-id="1e310-180">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="1e310-181">as</span><span class="sxs-lookup"><span data-stu-id="1e310-181">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="1e310-182">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="1e310-182">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
