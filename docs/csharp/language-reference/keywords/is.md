---
title: je - C# Odkaz
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399635"
---
# <a name="is-c-reference"></a><span data-ttu-id="379c6-102">is (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="379c6-102">is (C# Reference)</span></span>

<span data-ttu-id="379c6-103">Operátor `is` zkontroluje, zda je výsledek výrazu kompatibilní s daným typem, nebo (počínaje c# 7.0) testuje výraz proti vzoru.</span><span class="sxs-lookup"><span data-stu-id="379c6-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="379c6-104">Informace o operátoru `is` testování typu naleznete v části [is operátor](../operators/type-testing-and-cast.md#is-operator) v článku [Operátory testování typu a přetypovátí.](../operators/type-testing-and-cast.md)</span><span class="sxs-lookup"><span data-stu-id="379c6-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-cast.md#is-operator) section of the [Type-testing and cast operators](../operators/type-testing-and-cast.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="379c6-105">Porovnávání vzorů s`is`</span><span class="sxs-lookup"><span data-stu-id="379c6-105">Pattern matching with `is`</span></span>

<span data-ttu-id="379c6-106">Počínaje C# 7.0, `is` a [switch](switch.md) příkazy podporují porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="379c6-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="379c6-107">Klíčové `is` slovo podporuje následující vzory:</span><span class="sxs-lookup"><span data-stu-id="379c6-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="379c6-108">[Vzorek typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ, a pokud může být, přetypuje jej na proměnnou tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="379c6-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="379c6-109">[Konstantní vzor](#constant-pattern), který testuje, zda výraz vyhodnotí zadanou konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="379c6-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="379c6-110">[var pattern](#var-pattern), shoda, která vždy uspěje a váže hodnotu výrazu na novou místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="379c6-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="379c6-111">Vzor typu</span><span class="sxs-lookup"><span data-stu-id="379c6-111">Type pattern</span></span>

<span data-ttu-id="379c6-112">Při použití vzoru typu k `is` provedení porovnávání vzorků testuje, zda lze výraz převést na zadaný typ, a pokud může být, přetypuje do proměnné tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="379c6-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="379c6-113">Je to jednoduché rozšíření `is` prohlášení, které umožňuje stručné hodnocení typu a převod.</span><span class="sxs-lookup"><span data-stu-id="379c6-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="379c6-114">Obecná forma `is` vzoru typu je:</span><span class="sxs-lookup"><span data-stu-id="379c6-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="379c6-115">Kde *expr* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *expr* převeden, a `is` *varname* je objekt, na který je výsledek *expr* převeden, pokud je `true`test .</span><span class="sxs-lookup"><span data-stu-id="379c6-115">Where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span>

<span data-ttu-id="379c6-116">Výraz `is` je, `true` pokud *expr* není `null`a platí některá z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="379c6-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="379c6-117">*expr* je instancí stejného typu jako *typ*.</span><span class="sxs-lookup"><span data-stu-id="379c6-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="379c6-118">*expr* je instancí typu, který je odvozen od *typu*.</span><span class="sxs-lookup"><span data-stu-id="379c6-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="379c6-119">Jinými slovy, výsledek *expr* může být upcast na instanci *typu*.</span><span class="sxs-lookup"><span data-stu-id="379c6-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="379c6-120">*expr* má typ kompilace, který je základní třídou *typu*, a *expr* má typ runtime, který je *typu* nebo je odvozen od *typu*.</span><span class="sxs-lookup"><span data-stu-id="379c6-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="379c6-121">Typ proměnné v *době kompilace* je typ proměnné, jak je definován v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="379c6-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="379c6-122">*Typ runtime* proměnné je typ instance, která je přiřazena k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="379c6-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="379c6-123">*expr* je instancí třídy typu, který implementuje *rozhraní typu.*</span><span class="sxs-lookup"><span data-stu-id="379c6-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="379c6-124">Počínaje C# 7.1 *expr* může mít typ kompilace definovaný parametrem obecného typu a jeho omezeními.</span><span class="sxs-lookup"><span data-stu-id="379c6-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="379c6-125">Pokud *expr* `true` je a `is` `if` používá se s příkazem, *varname* je přiřazen a to pouze v rámci příkazu. `if`</span><span class="sxs-lookup"><span data-stu-id="379c6-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="379c6-126">Obor *varname* je z `is` výrazu na konec bloku `if` ohraničující příkaz.</span><span class="sxs-lookup"><span data-stu-id="379c6-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="379c6-127">Použití *varname* v jiném umístění generuje chybu v době kompilace pro použití proměnné, která nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="379c6-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="379c6-128">Následující příklad používá `is` vzorek typu k zajištění implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.</span><span class="sxs-lookup"><span data-stu-id="379c6-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="379c6-129">Bez porovnávání vzorů může být tento kód zapsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="379c6-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="379c6-130">Použití odpovídající vzorek typu vytváří kompaktnější, čitelný kód tím, že eliminuje potřebu `null`otestovat, zda je výsledkem převodu .</span><span class="sxs-lookup"><span data-stu-id="379c6-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="379c6-131">Vzorek `is` typu také vytváří kompaktnější kód při určování typu typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="379c6-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="379c6-132">Následující příklad používá `is` vzorek typu k určení, `Person` zda `Dog` je objekt nebo instance před zobrazením hodnoty příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="379c6-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="379c6-133">Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="379c6-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="379c6-134">Konstantní vzor</span><span class="sxs-lookup"><span data-stu-id="379c6-134">Constant pattern</span></span>

<span data-ttu-id="379c6-135">Při porovnávání vzorků s konstantním vzorkem testuje, `is` zda se výraz rovná zadané konstantě.</span><span class="sxs-lookup"><span data-stu-id="379c6-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="379c6-136">V C# 6 a starší verze konstantní vzor je podporován [příkazem switch.](switch.md)</span><span class="sxs-lookup"><span data-stu-id="379c6-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="379c6-137">Počínaje C# 7.0, je podporován `is` prohlášení také.</span><span class="sxs-lookup"><span data-stu-id="379c6-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="379c6-138">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="379c6-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="379c6-139">kde *expr* je výraz k vyhodnocení a *konstanta* je hodnota, pro kterou se má testovat.</span><span class="sxs-lookup"><span data-stu-id="379c6-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="379c6-140">*konstanta* může být některý z následujících konstantních výrazů:</span><span class="sxs-lookup"><span data-stu-id="379c6-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="379c6-141">Doslovná hodnota.</span><span class="sxs-lookup"><span data-stu-id="379c6-141">A literal value.</span></span>

- <span data-ttu-id="379c6-142">Název deklarované `const` proměnné.</span><span class="sxs-lookup"><span data-stu-id="379c6-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="379c6-143">Konstanta výčtu.</span><span class="sxs-lookup"><span data-stu-id="379c6-143">An enumeration constant.</span></span>

<span data-ttu-id="379c6-144">Konstantní výraz je vyhodnocen takto:</span><span class="sxs-lookup"><span data-stu-id="379c6-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="379c6-145">Pokud *expr* a *konstanta* jsou integrální typy, c# operátor rovnosti určuje, zda výraz vrátí `true` (to znamená, zda `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="379c6-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="379c6-146">Jinak je hodnota výrazu určena voláním statické [metody Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))</span><span class="sxs-lookup"><span data-stu-id="379c6-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="379c6-147">Následující příklad kombinuje text a konstantní vzorky k testování, zda je objekt `Dice` instance a pokud je, chcete-li zjistit, zda je hodnota kostky hod u 6.</span><span class="sxs-lookup"><span data-stu-id="379c6-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="379c6-148">Kontrola pro `null` lze provést pomocí konstantní vzor.</span><span class="sxs-lookup"><span data-stu-id="379c6-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="379c6-149">Klíčové `null` slovo je `is` podporováno příkazem.</span><span class="sxs-lookup"><span data-stu-id="379c6-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="379c6-150">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="379c6-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="379c6-151">Následující příklad ukazuje porovnání `null` kontrol:</span><span class="sxs-lookup"><span data-stu-id="379c6-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="379c6-152">var vzor</span><span class="sxs-lookup"><span data-stu-id="379c6-152">var pattern</span></span>

<span data-ttu-id="379c6-153">Vzor shoda se `var` vzorem vždy úspěšné.</span><span class="sxs-lookup"><span data-stu-id="379c6-153">A pattern match with the `var` pattern always succeeds.</span></span> <span data-ttu-id="379c6-154">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="379c6-154">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="379c6-155">Kde je hodnota *expr* vždy přiřazena místní proměnné s názvem *varname*.</span><span class="sxs-lookup"><span data-stu-id="379c6-155">Where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="379c6-156">*varname* je proměnná stejného typu jako typ *expr*v době kompilace .</span><span class="sxs-lookup"><span data-stu-id="379c6-156">*varname* is a variable of the same type as the compile-time type of *expr*.</span></span>

<span data-ttu-id="379c6-157">Pokud *expr* vyhodnotí `null`, `is` výraz vytvoří `true` a přiřadí `null` *varname*.</span><span class="sxs-lookup"><span data-stu-id="379c6-157">If *expr* evaluates to `null`, the `is` expression produces `true` and assigns `null` to *varname*.</span></span> <span data-ttu-id="379c6-158">Vzor var je jedním z `is` mála použití, které vytváří `true` pro hodnotu. `null`</span><span class="sxs-lookup"><span data-stu-id="379c6-158">The var pattern is one of the few uses of `is` that produces `true` for a `null` value.</span></span>

<span data-ttu-id="379c6-159">`var` Vzor můžete použít k vytvoření dočasné proměnné v logickém výrazu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="379c6-159">You can use the `var` pattern to create a temporary variable within a Boolean expression, as the following example shows:</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="379c6-160">V předchozím příkladu se dočasná proměnná používá k uložení výsledku nákladné operace.</span><span class="sxs-lookup"><span data-stu-id="379c6-160">In the preceding example, the temporary variable is used to store the result of an expensive operation.</span></span> <span data-ttu-id="379c6-161">Proměnnou lze pak použít vícekrát.</span><span class="sxs-lookup"><span data-stu-id="379c6-161">The variable can then be used multiple times.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="379c6-162">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="379c6-162">C# language specification</span></span>
  
<span data-ttu-id="379c6-163">Další informace naleznete v části [Is operátor](~/_csharplang/spec/expressions.md#the-is-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md) a následující návrhy jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="379c6-163">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="379c6-164">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="379c6-164">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="379c6-165">Porovnávání vzorů s obecnými typy</span><span class="sxs-lookup"><span data-stu-id="379c6-165">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="379c6-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="379c6-166">See also</span></span>

- [<span data-ttu-id="379c6-167">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="379c6-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="379c6-168">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="379c6-168">C# keywords</span></span>](index.md)
- [<span data-ttu-id="379c6-169">Operátory pro testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="379c6-169">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
