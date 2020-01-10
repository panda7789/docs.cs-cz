---
title: Implicitně typované lokální proměnné – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 692a0f8ad933f3ba4bef50681cb3487fa0a7eea9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714838"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="f3fec-102">Implicitně typované lokální proměnné (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="f3fec-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="f3fec-103">Lokální proměnné lze deklarovat bez poskytnutí explicitního typu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="f3fec-104">Klíčové slovo `var` instruuje kompilátor, aby odvodí typ proměnné z výrazu na pravé straně příkazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="f3fec-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="f3fec-105">Odvozený typ může být vestavěný typ, anonymní typ, uživatelsky definovaný typ nebo typ definovaný v knihovně tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3fec-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="f3fec-106">Další informace o tom, jak inicializovat pole pomocí `var`, naleznete v tématu [implicitně typované pole](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="f3fec-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="f3fec-107">Následující příklady znázorňují různé způsoby, jak lze pomocí `var`deklarovat místní proměnné:</span><span class="sxs-lookup"><span data-stu-id="f3fec-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="f3fec-108">Je důležité pochopit, že klíčové slovo `var` neznamená "variantu" a neindikuje, že proměnná je volně zadaná nebo má pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="f3fec-109">Pouze to znamená, že kompilátor určí a přiřadí nejvhodnější typ.</span><span class="sxs-lookup"><span data-stu-id="f3fec-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="f3fec-110">Klíčové slovo `var` může být použito v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="f3fec-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="f3fec-111">Na místních proměnných (proměnné deklarované v oboru metody), jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="f3fec-112">V příkazu [for](../../language-reference/keywords/for.md) Initialization.</span><span class="sxs-lookup"><span data-stu-id="f3fec-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="f3fec-113">V příkazu [foreach](../../language-reference/keywords/foreach-in.md) Initialization.</span><span class="sxs-lookup"><span data-stu-id="f3fec-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="f3fec-114">V příkazu [using](../../language-reference/keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="f3fec-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="f3fec-115">Další informace najdete v tématu [použití implicitního typu lokálních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="f3fec-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="f3fec-116">var a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f3fec-116">var and anonymous types</span></span>

<span data-ttu-id="f3fec-117">V mnoha případech je použití `var` volitelné a je pouze syntaktické pohodlí.</span><span class="sxs-lookup"><span data-stu-id="f3fec-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="f3fec-118">Nicméně pokud je proměnná inicializována pomocí anonymního typu, je nutné deklarovat proměnnou jako `var`, pokud potřebujete získat přístup k vlastnostem objektu v pozdějším bodě.</span><span class="sxs-lookup"><span data-stu-id="f3fec-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="f3fec-119">Toto je běžný scénář ve výrazech dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="f3fec-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="f3fec-120">Další informace najdete v tématu [anonymní typy](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f3fec-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="f3fec-121">Z perspektivy zdrojového kódu nemá anonymní typ žádný název.</span><span class="sxs-lookup"><span data-stu-id="f3fec-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="f3fec-122">Proto pokud byla proměnná dotazu inicializována pomocí `var`, pak jediným způsobem, jak získat přístup k vlastnostem v vrácené sekvenci objektů, je použití `var` jako typ proměnné iterace v příkazu `foreach`.</span><span class="sxs-lookup"><span data-stu-id="f3fec-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="f3fec-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3fec-123">Remarks</span></span>

<span data-ttu-id="f3fec-124">Následující omezení platí pro implicitně typové deklarace proměnných:</span><span class="sxs-lookup"><span data-stu-id="f3fec-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="f3fec-125">`var` lze použít pouze v případě, že je místní proměnná deklarována a inicializována v rámci stejného příkazu; proměnnou nelze inicializovat na hodnotu null nebo do skupiny metod nebo do anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="f3fec-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="f3fec-126">`var` nelze použít pro pole v oboru třídy.</span><span class="sxs-lookup"><span data-stu-id="f3fec-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="f3fec-127">Proměnné deklarované pomocí `var` nelze použít ve výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="f3fec-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="f3fec-128">Jinými slovy, tento výraz je platný: `int i = (i = 20);` ale tento výraz vytvoří chybu při kompilaci: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="f3fec-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="f3fec-129">V rámci stejného příkazu nelze inicializovat více proměnných s implicitním typem.</span><span class="sxs-lookup"><span data-stu-id="f3fec-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="f3fec-130">Pokud je typ s názvem `var` v oboru, pak bude klíčové slovo `var` přeloženo na tento název typu a nebude zpracováno jako součást implicitně typové deklarace lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="f3fec-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="f3fec-131">Implicitní zadání pomocí klíčového slova `var` lze použít pouze pro proměnné v oboru místních metod.</span><span class="sxs-lookup"><span data-stu-id="f3fec-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="f3fec-132">Implicitní psaní není k dispozici pro pole třídy, C# protože by Kompilátor narazil na logický Paradox při zpracování kódu: kompilátor musí znát typ pole, ale nemůže určit typ, dokud není výraz přiřazení analyzován, a výraz nelze vyhodnotit bez znalosti typu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="f3fec-133">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f3fec-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="f3fec-134">`bookTitles` je pole třídy pro daný typ `var`.</span><span class="sxs-lookup"><span data-stu-id="f3fec-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="f3fec-135">Vzhledem k tomu, že pole nemá žádný výraz k vyhodnocení, není možné, aby kompilátor odvodit, jaký typ `bookTitles` by měl být.</span><span class="sxs-lookup"><span data-stu-id="f3fec-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="f3fec-136">Kromě toho je také nedostatečné Přidání výrazu do pole (například pro místní proměnnou):</span><span class="sxs-lookup"><span data-stu-id="f3fec-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="f3fec-137">Když kompilátor narazí na pole během kompilování kódu, zaznamenává typ každého pole před zpracováním jakýchkoli výrazů, které jsou k němu přidruženy.</span><span class="sxs-lookup"><span data-stu-id="f3fec-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="f3fec-138">Kompilátor narazí na stejný Paradox, který se pokouší analyzovat `bookTitles`: musí znát typ pole, ale kompilátor obvykle určí `var`typ analýzou výrazu, který není možné bez vědomí typu předem.</span><span class="sxs-lookup"><span data-stu-id="f3fec-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="f3fec-139">Může se stát, že `var` mohou být užitečné také s výrazy dotazu, ve kterých je obtížné určit přesný konstruovaný typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="f3fec-140">K tomu může dojít při operacích seskupování a řazení.</span><span class="sxs-lookup"><span data-stu-id="f3fec-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="f3fec-141">Klíčové slovo `var` může být užitečné také v případě, že konkrétní typ proměnné je únavné pro psaní na klávesnici nebo je zřejmá nebo nepřidává k čitelnosti kódu.</span><span class="sxs-lookup"><span data-stu-id="f3fec-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="f3fec-142">Jeden příklad, kde je `var` užitečné tímto způsobem, je s vnořenými obecnými typy, jako jsou ty, které se používají při operacích skupiny.</span><span class="sxs-lookup"><span data-stu-id="f3fec-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="f3fec-143">V následujícím dotazu je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="f3fec-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="f3fec-144">Pokud vy a ostatní uživatelé, kteří musí tento kód pochopit, neexistují žádné potíže s používáním implicitního zadávání pro pohodlí a zkrácení.</span><span class="sxs-lookup"><span data-stu-id="f3fec-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="f3fec-145">Použití `var` však má alespoň potenciál, aby bylo obtížné pochopit kód pro jiné vývojáře.</span><span class="sxs-lookup"><span data-stu-id="f3fec-145">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="f3fec-146">V C# takovém případě dokumentace obecně používá `var` jenom v případě, že je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="f3fec-146">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3fec-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3fec-147">See also</span></span>

- [<span data-ttu-id="f3fec-148">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="f3fec-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="f3fec-149">Implicitně typovaná pole</span><span class="sxs-lookup"><span data-stu-id="f3fec-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="f3fec-150">Použití implicitního typu lokálních proměnných a polí ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="f3fec-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="f3fec-151">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f3fec-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="f3fec-152">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="f3fec-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="f3fec-153">var</span><span class="sxs-lookup"><span data-stu-id="f3fec-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="f3fec-154">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f3fec-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="f3fec-155">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="f3fec-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="f3fec-156">for</span><span class="sxs-lookup"><span data-stu-id="f3fec-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="f3fec-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="f3fec-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="f3fec-158">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="f3fec-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
