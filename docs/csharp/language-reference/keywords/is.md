---
title: je - C# odkaz
ms.custom: seodec18
ms.date: 04/09/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 79cc59eb8de513f547a8fd87db8c95dd9af37375
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754517"
---
# <a name="is-c-reference"></a><span data-ttu-id="3e33a-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3e33a-102">is (C# Reference)</span></span>

<span data-ttu-id="3e33a-103">Zkontroluje, jestli je objekt kompatibilní s daným typem, nebo (od verze C# 7.0) testuje výraz se vzorem.</span><span class="sxs-lookup"><span data-stu-id="3e33a-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="3e33a-104">Testování kompatibility typu</span><span class="sxs-lookup"><span data-stu-id="3e33a-104">Testing for type compatibility</span></span>

<span data-ttu-id="3e33a-105">`is` – Klíčové slovo vyhodnocen jako typ kompatibility za běhu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="3e33a-106">Určuje, zda instance objektu nebo výsledek výrazu lze převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="3e33a-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="3e33a-107">Má syntaxi</span><span class="sxs-lookup"><span data-stu-id="3e33a-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="3e33a-108">kde *expr* je výraz, který se vyhodnotí na instanci typu, a *typ* název typu, na který je výsledkem *expr* se má převést.</span><span class="sxs-lookup"><span data-stu-id="3e33a-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="3e33a-109">`is` Příkaz je `true` Pokud *expr* je null a objekt, který je výsledkem vyhodnocení výrazu může být převeden na *typ*; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="3e33a-110">Například následující kód určuje, zda `obj` lze převést na instanci `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="3e33a-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="3e33a-111">`is` Příkaz má hodnotu true pokud:</span><span class="sxs-lookup"><span data-stu-id="3e33a-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="3e33a-112">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="3e33a-113">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="3e33a-114">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="3e33a-115">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="3e33a-116">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3e33a-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="3e33a-117">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="3e33a-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="3e33a-118">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e33a-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="3e33a-119">Následující příklad ukazuje, že `is` výraz vyhodnocen jako `true` pro každou z těchto převodů.</span><span class="sxs-lookup"><span data-stu-id="3e33a-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="3e33a-120">`is` – Klíčové slovo vygeneruje upozornění kompilace, pokud je známo, že výraz vždy být buď `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="3e33a-121">Uvažuje pouze převody odkazů, převodu zabalení a rozbalení převody; nepovažuje uživatelem definované převody nebo převody definované typem [implicitní](implicit.md) a [explicitní](explicit.md) operátory.</span><span class="sxs-lookup"><span data-stu-id="3e33a-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="3e33a-122">Následující příklad generuje upozornění, protože výsledkem převodu je známá v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="3e33a-122">The following example generates warnings because the result of the conversion is known at compile time.</span></span> <span data-ttu-id="3e33a-123">`is` Výraz pro převod z `int` k `long` a `double` vrátí hodnotu false, protože tyto převody jsou zpracovávány [implicitní](implicit.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="3e33a-123">The `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="3e33a-124">`expr` nemůže být anonymní metody nebo lambda výrazu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-124">`expr` cannot be an anonymous method or lambda expression.</span></span> <span data-ttu-id="3e33a-125">Může být libovolný výraz, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-125">It can be any other expression that returns a value.</span></span> <span data-ttu-id="3e33a-126">Následující příklad používá `is` vyhodnotit vrácenou hodnotu volání metody.</span><span class="sxs-lookup"><span data-stu-id="3e33a-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="3e33a-127">Od verze C# 7.0, můžete použít porovnávání vzorů s [vzor typu](#type) zapsat stručnější kód, který používá `is` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-127">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="3e33a-128">Porovnávání vzorů s `is`</span><span class="sxs-lookup"><span data-stu-id="3e33a-128">Pattern matching with `is`</span></span>

<span data-ttu-id="3e33a-129">Od verze C# 7.0, `is` a [přepnout](../../../csharp/language-reference/keywords/switch.md) příkazy podpory porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="3e33a-129">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="3e33a-130">`is` – Klíčové slovo podporuje následující způsoby:</span><span class="sxs-lookup"><span data-stu-id="3e33a-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="3e33a-131">[Typ vzorku](#type), který testuje, jestli výraz lze převést na zadaný typ a, pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="3e33a-132">[Konstantní vzorek](#constant), který testuje, jestli je výraz vyhodnocen jako na zadanou hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="3e33a-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="3e33a-133">[vzor var](#var), shoda, který je vždy úspěšné a přiřazuje hodnotu výrazu nové místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="3e33a-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <a name="a-nametype-type-pattern"></a><span data-ttu-id="3e33a-134"><a name="type" />Vzorek typu</span><span class="sxs-lookup"><span data-stu-id="3e33a-134"><a name="type" />Type pattern</span></span>

<span data-ttu-id="3e33a-135">Při použití typu modelu k provádění porovnávání vzorů, `is` testuje výraz lze převést na zadaný typ a pokud jej lze přetypování pro proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="3e33a-136">Je jednoduché rozšíření `is` příkaz, který umožňuje stručný typ vyhodnocení a převodu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-136">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="3e33a-137">Obecný tvar `is` vzor typu je:</span><span class="sxs-lookup"><span data-stu-id="3e33a-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="3e33a-138">kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* se má převést a *název_proměnné* je objekt, na který výsledek *expr* je převedena, pokud `is` test je `true`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="3e33a-139">`is` Výraz je `true` Pokud *expr* není `null`, a je splněna některá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3e33a-139">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="3e33a-140">*výraz* je instance stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="3e33a-141">*výraz* je instance typu, který je odvozen od *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="3e33a-142">Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="3e33a-143">*výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="3e33a-144">*Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3e33a-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="3e33a-145">*Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="3e33a-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="3e33a-146">*výraz* je instance typu, který implementuje *typ* rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e33a-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="3e33a-147">Počínaje C# 7.1, *expr* může mít za kompilace typu definované v parametru obecného typu a jeho omezení.</span><span class="sxs-lookup"><span data-stu-id="3e33a-147">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span> 

<span data-ttu-id="3e33a-148">Pokud *expr* je `true` a `is` se používá s `if` příkazu *název_proměnné* přiřazují v rámci `if` pouze příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e33a-148">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="3e33a-149">Rozsah *název_proměnné* z `is` výraz na konci uzavírající blok `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-149">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="3e33a-150">Pomocí *název_proměnné* v jiném umístění vygeneruje chybu kompilace pro použití proměnné, která nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="3e33a-150">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="3e33a-151">V následujícím příkladu `is` vzor typu k dispozici implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3e33a-151">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="3e33a-152">Bez porovnávání vzorů, může být napsán takto následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3e33a-152">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="3e33a-153">Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-153">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="3e33a-154">`is` Vzor typu také vytvoří kompaktnějším kód při určování typu hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-154">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="3e33a-155">V následujícím příkladu `is` vzor typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnota příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3e33a-155">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="3e33a-156">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, který obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="3e33a-156">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="3e33a-157"><a name="constant" /> Konstantní vzorek</span><span class="sxs-lookup"><span data-stu-id="3e33a-157"><a name="constant" /> Constant pattern</span></span>

<span data-ttu-id="3e33a-158">Při provádění porovnávání vzorů s konstantní vzorek `is` testuje, zda výraz rovná zadané – konstanta.</span><span class="sxs-lookup"><span data-stu-id="3e33a-158">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="3e33a-159">V jazyce C# 6 a starší verze, je podporován konstantní vzorek [přepnout](switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-159">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="3e33a-160">Počínaje C# 7.0, je podporována `is` také příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e33a-160">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="3e33a-161">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3e33a-161">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="3e33a-162">kde *expr* je výraz k vyhodnocení, a *konstantní* je hodnota pro testování.</span><span class="sxs-lookup"><span data-stu-id="3e33a-162">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="3e33a-163">*konstantní* může být následující konstantní výrazy:</span><span class="sxs-lookup"><span data-stu-id="3e33a-163">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="3e33a-164">Hodnota literálu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-164">A literal value.</span></span>

- <span data-ttu-id="3e33a-165">Název deklarovanou `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="3e33a-165">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="3e33a-166">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-166">An enumeration constant.</span></span>

<span data-ttu-id="3e33a-167">Konstantní výraz je vyhodnocen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3e33a-167">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="3e33a-168">Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="3e33a-168">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="3e33a-169">V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="3e33a-169">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="3e33a-170">Následující příklad kombinuje typ a konstantní vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, k určení, zda dice kumulativní hodnotu 6.</span><span class="sxs-lookup"><span data-stu-id="3e33a-170">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="3e33a-171">Kontrola `null` je možné provádět pomocí konstantní vzorek.</span><span class="sxs-lookup"><span data-stu-id="3e33a-171">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="3e33a-172">`null` – Klíčové slovo je podporován `is` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e33a-172">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="3e33a-173">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3e33a-173">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="3e33a-174">Následující příklad ukazuje porovnání `null` ověří:</span><span class="sxs-lookup"><span data-stu-id="3e33a-174">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="3e33a-175"><a name="var" /> vzor var </a></span><span class="sxs-lookup"><span data-stu-id="3e33a-175"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="3e33a-176">`var` Vzor je pokrývající vše pro libovolným typem nebo hodnotou.</span><span class="sxs-lookup"><span data-stu-id="3e33a-176">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="3e33a-177">Hodnota *expr* se vždycky přiřazuje lokální proměnná stejný typ jako typ času kompilace *expr*.</span><span class="sxs-lookup"><span data-stu-id="3e33a-177">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="3e33a-178">Výsledkem `is` výraz je vždycky `true`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-178">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="3e33a-179">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="3e33a-179">Its syntax is:</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="3e33a-180">Následující příklad používá vzor var výrazu přiřazení k proměnné s názvem `obj`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-180">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="3e33a-181">Potom zobrazí hodnotu a typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="3e33a-181">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="3e33a-182">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e33a-182">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e33a-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e33a-183">See also</span></span>

- [<span data-ttu-id="3e33a-184">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e33a-184">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3e33a-185">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e33a-185">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="3e33a-186">typeof</span><span class="sxs-lookup"><span data-stu-id="3e33a-186">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="3e33a-187">as</span><span class="sxs-lookup"><span data-stu-id="3e33a-187">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="3e33a-188">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="3e33a-188">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
