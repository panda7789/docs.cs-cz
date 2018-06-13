---
title: is (Referenční dokumentace jazyka C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: c01152d016a852c15ffa1d1c82c16d6795965f31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289214"
---
# <a name="is-c-reference"></a><span data-ttu-id="60d00-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="60d00-102">is (C# Reference)</span></span> #

<span data-ttu-id="60d00-103">Zkontroluje, jestli je objekt kompatibilní s daného typu, nebo (C# 7.0 počínaje) testy výraz se vzorem.</span><span class="sxs-lookup"><span data-stu-id="60d00-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="60d00-104">Testování kompatibility typu</span><span class="sxs-lookup"><span data-stu-id="60d00-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="60d00-105">`is` – Klíčové slovo vyhodnotí kompatibility typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="60d00-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="60d00-106">Určuje, zda instanci objektu nebo výsledek výrazu lze převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="60d00-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="60d00-107">Má syntaxe</span><span class="sxs-lookup"><span data-stu-id="60d00-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="60d00-108">kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* je název typu, na který výsledek *expr* chcete převést.</span><span class="sxs-lookup"><span data-stu-id="60d00-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="60d00-109">`is` Příkaz je `true` Pokud *expr* jinou hodnotu než null a objekt, který výsledků vyhodnocení výrazu může být převeden na *typ*, jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="60d00-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="60d00-110">Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="60d00-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="60d00-111">`is` Příkaz je hodnota true, pokud:</span><span class="sxs-lookup"><span data-stu-id="60d00-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="60d00-112">*Expr* je instance stejného typu jako *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="60d00-113">*Expr* představuje instanci typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="60d00-114">Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="60d00-115">*Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="60d00-116">*Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="60d00-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="60d00-117">*Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="60d00-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="60d00-118">*Expr* představuje instanci typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60d00-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="60d00-119">Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převody.</span><span class="sxs-lookup"><span data-stu-id="60d00-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="60d00-120">`is` – Klíčové slovo vygeneruje kompilaci upozornění, pokud je znám výraz vždycky být buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="60d00-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="60d00-121">Uvažuje pouze převody odkazů, převodů zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="60d00-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="60d00-122">V následujícím příkladu generuje upozornění, protože je v době kompilace výsledek převodu.</span><span class="sxs-lookup"><span data-stu-id="60d00-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="60d00-123">Všimněte si, že `is` výraz převody z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="60d00-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="60d00-124">`expr` může být jakékoli výraz, který vrátí hodnotu, s výjimkou anonymní metody a výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="60d00-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="60d00-125">Následující příklad používá `is` vyhodnotit návratovou hodnotu volání metody.</span><span class="sxs-lookup"><span data-stu-id="60d00-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="60d00-126">Od verze 7.0 C#, můžete použít porovnávání vzorů s [typ vzor](#type) napsat přesnější kód, který používá `is` příkaz.</span><span class="sxs-lookup"><span data-stu-id="60d00-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="60d00-127">Pro porovnávání s `is`</span><span class="sxs-lookup"><span data-stu-id="60d00-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="60d00-128">Od verze jazyka C# 7.0, `is` a [přepínače](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="60d00-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="60d00-129">`is` – Klíčové slovo podporuje následující vzorce:</span><span class="sxs-lookup"><span data-stu-id="60d00-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="60d00-130">[Typ vzor](#type), který kontroluje, zda výraz lze převést na zadaný typ a, pokud lze, obsahuje ji proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="60d00-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="60d00-131">[Konstantní vzor](#constant), který kontroluje, zda výsledkem konstantní hodnotu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="60d00-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="60d00-132">[var – vzor](#var), shoda, který vždy úspěšné a sváže hodnotu výrazu nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="60d00-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="60d00-133"><a name="type" /> Typ vzor </a></span><span class="sxs-lookup"><span data-stu-id="60d00-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="60d00-134">Při provádění porovnávání vzorů pomocí vzoru typ `is` testuje, zda výraz lze převést na zadaný typ a pokud jej lze obsahuje ji proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="60d00-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="60d00-135">Je přehledné rozšíření `is` příkaz, který umožňuje stručným typ vyhodnocení a převod.</span><span class="sxs-lookup"><span data-stu-id="60d00-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="60d00-136">Obecná forma `is` typ vzor je:</span><span class="sxs-lookup"><span data-stu-id="60d00-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="60d00-137">kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* chcete převést a *název_proměnné* je objekt, ke kterému výsledek *expr* je převést, pokud `is` test je `true`.</span><span class="sxs-lookup"><span data-stu-id="60d00-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="60d00-138">`is` Výraz `true` Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="60d00-138">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="60d00-139">*Expr* je instance stejného typu jako *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="60d00-140">*Expr* představuje instanci typu, která je odvozena z *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="60d00-141">Jinými slovy, výsledek *expr* může být přetypování nahoru na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="60d00-142">*Expr* má kompilaci typ, který je základní třídě *typ*, a *expr* má typ modulu runtime, který je *typ* nebo je odvozený od *typu*.</span><span class="sxs-lookup"><span data-stu-id="60d00-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="60d00-143">*Typu v čase kompilace* proměnné je typ proměnné, jak jsou definovány v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="60d00-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="60d00-144">*Typ modulu runtime* proměnné je typ instanci, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="60d00-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="60d00-145">*Expr* představuje instanci typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60d00-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="60d00-146">Pokud *exp* je `true` a `is` se používá s `if` příkaz *název_proměnné* je přiřazen a má místní rozsah v rámci `if` pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="60d00-146">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="60d00-147">Následující příklad používá `is` typ vzor k zajištění implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="60d00-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="60d00-148">Bez porovnávání vzorů, může tento kód zapsat takto.</span><span class="sxs-lookup"><span data-stu-id="60d00-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="60d00-149">Použití porovnávání vzorů typu vytváří odstraněním potřeba otestovat, zda je výsledek převodu z kódu kompaktnější a čitelné `null`.</span><span class="sxs-lookup"><span data-stu-id="60d00-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="60d00-150">`is` Typ vzor také vytváří kompaktnější kód při určování typ typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60d00-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="60d00-151">Následující příklad používá `is` typ vzor k určení, zda je objekt `Person` nebo `Dog` instance, než se zobrazí hodnota příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="60d00-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="60d00-152">Kód ekvivalentní bez odpovídající vzor vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="60d00-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="60d00-153"><a name="constant" /> Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="60d00-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="60d00-154">Při provádění porovnávání s konstantní vzor vzorů `is` testuje, zda výraz rovná zadané konstanta.</span><span class="sxs-lookup"><span data-stu-id="60d00-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="60d00-155">V jazyce C# 6 a starší verze, konstantní vzor podporuje [přepínač](switch.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="60d00-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="60d00-156">Od verze 7.0 C#, je podporována `is` příkaz také.</span><span class="sxs-lookup"><span data-stu-id="60d00-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="60d00-157">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="60d00-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="60d00-158">kde *expr* se výraz, který chcete vyhodnotit, a *konstantní* je hodnota, kterou chcete otestovat.</span><span class="sxs-lookup"><span data-stu-id="60d00-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="60d00-159">*konstantní* může být libovolná z následujících konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="60d00-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="60d00-160">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="60d00-160">A literal value.</span></span>

- <span data-ttu-id="60d00-161">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="60d00-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="60d00-162">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="60d00-162">An enumeration constant.</span></span>

<span data-ttu-id="60d00-163">Konstantní výraz je vyhodnotit takto:</span><span class="sxs-lookup"><span data-stu-id="60d00-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="60d00-164">Pokud *expr* a *konstantní* jsou integrální typy operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="60d00-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="60d00-165">Jinak hodnota výrazu je určena voláním statických [Object.Equals (výraz, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metoda.</span><span class="sxs-lookup"><span data-stu-id="60d00-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="60d00-166">Následující příklad kombinuje typu a konstanta vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, chcete-li zjistit jestli rozčlenění kumulativní hodnotu 6.</span><span class="sxs-lookup"><span data-stu-id="60d00-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="60d00-167"><a name="var" /> var – vzor </a></span><span class="sxs-lookup"><span data-stu-id="60d00-167"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="60d00-168">Vzor shody s var vzor je vždy úspěšné.</span><span class="sxs-lookup"><span data-stu-id="60d00-168">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="60d00-169">Jeho syntaxe je</span><span class="sxs-lookup"><span data-stu-id="60d00-169">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="60d00-170">kde hodnota *expr* se vždycky přiřazuje místní proměnné s názvem *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="60d00-170">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="60d00-171">*název_proměnné* je statická proměnná stejného typu jako *expr*.</span><span class="sxs-lookup"><span data-stu-id="60d00-171">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="60d00-172">Následující příklad používá var vzor výrazu přiřadit proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="60d00-172">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="60d00-173">Potom zobrazí hodnota a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="60d00-173">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="60d00-174">Všimněte si, že pokud *expr* je `null`, `is` výraz stále platí a přiřadí `null` k *název_proměnné*.</span><span class="sxs-lookup"><span data-stu-id="60d00-174">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="60d00-175">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60d00-175">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60d00-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="60d00-176">See also</span></span>  
 [<span data-ttu-id="60d00-177">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60d00-177">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="60d00-178">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60d00-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="60d00-179">typeof</span><span class="sxs-lookup"><span data-stu-id="60d00-179">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="60d00-180">as</span><span class="sxs-lookup"><span data-stu-id="60d00-180">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="60d00-181">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="60d00-181">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
