---
title: Částečné třídy a metody – Průvodce programováním v C#
description: Částečné třídy a metody v jazyce C# rozdělí definici třídy, struktury, rozhraní nebo metody přes dva nebo více zdrojových souborů.
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 792159786131654d6ee0363f7ab7b87ac50d32bb
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864745"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="b434b-103">Částečné třídy a metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b434b-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="b434b-104">Je možné rozdělit definici [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md), [rozhraní](../../language-reference/keywords/interface.md) nebo metody přes dva nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="b434b-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="b434b-105">Každý zdrojový soubor obsahuje oddíl definice typu nebo metody a všechny části jsou kombinovány při kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="b434b-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="b434b-106">Částečné třídy</span><span class="sxs-lookup"><span data-stu-id="b434b-106">Partial Classes</span></span>

<span data-ttu-id="b434b-107">Je žádoucí rozdělit definici třídy na několik situací:</span><span class="sxs-lookup"><span data-stu-id="b434b-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="b434b-108">Při práci na rozsáhlých projektech umožňuje rozprostření třídy přes samostatné soubory současně pracovat s více programátory.</span><span class="sxs-lookup"><span data-stu-id="b434b-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="b434b-109">Při práci s automaticky generovaným zdrojem lze kód přidat do třídy, aniž by bylo nutné znovu vytvořit zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="b434b-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="b434b-110">Visual Studio používá tento přístup při vytváření model Windows Forms, kódu obálky webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b434b-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="b434b-111">Můžete vytvořit kód, který používá tyto třídy, aniž byste museli upravovat soubor vytvořený v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b434b-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="b434b-112">Chcete-li rozdělit definici třídy, použijte modifikátor klíčového slova [Partial](../../language-reference/keywords/partial-type.md) , jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b434b-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="b434b-113">`partial`Klíčové slovo označuje, že v oboru názvů lze definovat jiné části třídy, struktury nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b434b-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="b434b-114">Všechny části musí používat `partial` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b434b-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="b434b-115">Všechny části musí být k dispozici v době kompilace, aby bylo možné vytvořit konečný typ.</span><span class="sxs-lookup"><span data-stu-id="b434b-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="b434b-116">Všechny části musí mít stejnou přístupnost, například `public` , `private` a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b434b-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="b434b-117">Je-li kterákoli část deklarována jako abstraktní, pak je celý typ považován za abstraktní.</span><span class="sxs-lookup"><span data-stu-id="b434b-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="b434b-118">Je-li kterákoli část deklarována jako zapečetěná, je celý typ považován za zapečetěný.</span><span class="sxs-lookup"><span data-stu-id="b434b-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="b434b-119">Pokud jakákoli část deklaruje základní typ, pak celý typ zdědí tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="b434b-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="b434b-120">Všechny části, které určují základní třídu, musí souhlasit, ale části, které vynechávají základní třídu, stále zdědí základní typ.</span><span class="sxs-lookup"><span data-stu-id="b434b-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="b434b-121">Části mohou určovat odlišná základní rozhraní a konečný typ implementuje všechna rozhraní uvedená všemi částečnými deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="b434b-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="b434b-122">Všechny členy třídy, struktury nebo rozhraní deklarované v částečné definici jsou k dispozici pro všechny ostatní části.</span><span class="sxs-lookup"><span data-stu-id="b434b-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="b434b-123">Konečný typ je kombinace všech částí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="b434b-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="b434b-124">`partial`Modifikátor není k dispozici pro deklarace delegáta nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="b434b-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="b434b-125">Následující příklad ukazuje, že vnořené typy mohou být částečné, i když typ, který je vnořen do, není částečně sám.</span><span class="sxs-lookup"><span data-stu-id="b434b-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="b434b-126">V době kompilace jsou sloučeny atributy definicí částečného typu.</span><span class="sxs-lookup"><span data-stu-id="b434b-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="b434b-127">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="b434b-127">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="b434b-128">Jsou ekvivalentem následujících deklarací:</span><span class="sxs-lookup"><span data-stu-id="b434b-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="b434b-129">Následující jsou sloučeny ze všech definicí částečného typu:</span><span class="sxs-lookup"><span data-stu-id="b434b-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="b434b-130">Komentáře XML</span><span class="sxs-lookup"><span data-stu-id="b434b-130">XML comments</span></span>

- <span data-ttu-id="b434b-131">rozhraní</span><span class="sxs-lookup"><span data-stu-id="b434b-131">interfaces</span></span>

- <span data-ttu-id="b434b-132">atributy parametru obecného typu</span><span class="sxs-lookup"><span data-stu-id="b434b-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="b434b-133">class – atributy</span><span class="sxs-lookup"><span data-stu-id="b434b-133">class attributes</span></span>

- <span data-ttu-id="b434b-134">členy</span><span class="sxs-lookup"><span data-stu-id="b434b-134">members</span></span>

<span data-ttu-id="b434b-135">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="b434b-135">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="b434b-136">Jsou ekvivalentem následujících deklarací:</span><span class="sxs-lookup"><span data-stu-id="b434b-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="b434b-137">Omezení</span><span class="sxs-lookup"><span data-stu-id="b434b-137">Restrictions</span></span>

<span data-ttu-id="b434b-138">Při práci s definicemi částečné třídy je potřeba provést několik pravidel:</span><span class="sxs-lookup"><span data-stu-id="b434b-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="b434b-139">Všechny definice částečného typu, které by měly být součástí stejného typu, musí být upraveny pomocí `partial` .</span><span class="sxs-lookup"><span data-stu-id="b434b-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="b434b-140">Například následující deklarace tříd generují chybu:</span><span class="sxs-lookup"><span data-stu-id="b434b-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="b434b-141">`partial`Modifikátor se může objevit pouze bezprostředně před klíčovými slovy `class` , `struct` nebo `interface` .</span><span class="sxs-lookup"><span data-stu-id="b434b-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="b434b-142">Vnořené částečné typy jsou povoleny v definicích částečného typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b434b-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="b434b-143">Všechny definice částečného typu, které by měly být součástí stejného typu, musí být definovány ve stejném sestavení a stejném modulu (soubor. exe nebo. dll).</span><span class="sxs-lookup"><span data-stu-id="b434b-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="b434b-144">Částečné definice nemůžou zahrnovat víc modulů.</span><span class="sxs-lookup"><span data-stu-id="b434b-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="b434b-145">Název třídy a parametry obecného typu se musí shodovat se všemi definicemi částečného typu.</span><span class="sxs-lookup"><span data-stu-id="b434b-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="b434b-146">Obecné typy mohou být částečné.</span><span class="sxs-lookup"><span data-stu-id="b434b-146">Generic types can be partial.</span></span> <span data-ttu-id="b434b-147">Každá částečná deklarace musí používat stejné názvy parametrů ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b434b-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="b434b-148">Následující klíčová slova v definici částečného typu jsou volitelná, ale pokud jsou k dispozici v rámci jedné definice částečného typu, nemůže být v konfliktu s klíčovými slovy zadanými v jiné částečné definici pro stejný typ:</span><span class="sxs-lookup"><span data-stu-id="b434b-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="b434b-149">public</span><span class="sxs-lookup"><span data-stu-id="b434b-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="b434b-150">hlášen</span><span class="sxs-lookup"><span data-stu-id="b434b-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="b434b-151">protected</span><span class="sxs-lookup"><span data-stu-id="b434b-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="b434b-152">internal</span><span class="sxs-lookup"><span data-stu-id="b434b-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="b434b-153">Výtah</span><span class="sxs-lookup"><span data-stu-id="b434b-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="b434b-154">sealed</span><span class="sxs-lookup"><span data-stu-id="b434b-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="b434b-155">base – třída</span><span class="sxs-lookup"><span data-stu-id="b434b-155">base class</span></span>

  - <span data-ttu-id="b434b-156">[Nový](../../language-reference/keywords/new-modifier.md) modifikátor (vnořené části)</span><span class="sxs-lookup"><span data-stu-id="b434b-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="b434b-157">obecná omezení</span><span class="sxs-lookup"><span data-stu-id="b434b-157">generic constraints</span></span>

<span data-ttu-id="b434b-158">Další informace najdete v tématu [omezení parametrů typu](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b434b-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="b434b-159">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b434b-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="b434b-160">Popis</span><span class="sxs-lookup"><span data-stu-id="b434b-160">Description</span></span>

<span data-ttu-id="b434b-161">V následujícím příkladu jsou pole a konstruktor třídy `Coords` deklarovány v jedné definici částečné třídy a člen `PrintCoords` je deklarován v jiné definici částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="b434b-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="b434b-162">Kód</span><span class="sxs-lookup"><span data-stu-id="b434b-162">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="b434b-163">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="b434b-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="b434b-164">Popis</span><span class="sxs-lookup"><span data-stu-id="b434b-164">Description</span></span>

<span data-ttu-id="b434b-165">Následující příklad ukazuje, že můžete také vyvíjet částečné struktury a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b434b-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="b434b-166">Kód</span><span class="sxs-lookup"><span data-stu-id="b434b-166">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="b434b-167">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="b434b-167">Partial Methods</span></span>

<span data-ttu-id="b434b-168">Částečná třída nebo struktura může obsahovat částečnou metodu.</span><span class="sxs-lookup"><span data-stu-id="b434b-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="b434b-169">Jedna část třídy obsahuje signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="b434b-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="b434b-170">Volitelná implementace může být definována ve stejné části nebo jiné části.</span><span class="sxs-lookup"><span data-stu-id="b434b-170">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="b434b-171">Pokud není implementována implementace, pak je metoda a všechna volání metody odebrána v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="b434b-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="b434b-172">Částečné metody umožňují, aby implementátor jednoho dílu třídy definoval metodu, podobně jako událost.</span><span class="sxs-lookup"><span data-stu-id="b434b-172">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="b434b-173">Implementátor druhé části třídy se může rozhodnout, zda má být metoda implementována.</span><span class="sxs-lookup"><span data-stu-id="b434b-173">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="b434b-174">Pokud není metoda implementována, kompilátor odstraní signaturu metody a všechna volání metody.</span><span class="sxs-lookup"><span data-stu-id="b434b-174">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="b434b-175">Volání metody, včetně všech výsledků, které by byly provedeny z vyhodnocení argumentů v volání, nemají za běhu žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="b434b-175">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="b434b-176">Proto jakýkoli kód v částečné třídě může volně použít částečnou metodu, i když není zadaná implementace.</span><span class="sxs-lookup"><span data-stu-id="b434b-176">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="b434b-177">Pokud je metoda volána, ale není implementována, nebudou výsledkem žádné chyby při kompilaci nebo běhové chyby.</span><span class="sxs-lookup"><span data-stu-id="b434b-177">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="b434b-178">Částečné metody jsou obzvláště užitečné jako způsob přizpůsobení vygenerovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b434b-178">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="b434b-179">Umožňují vyhradit název metody a signaturu, aby vygenerovaný kód mohl volat metodu, ale vývojář se může rozhodnout, zda metodu implementovat.</span><span class="sxs-lookup"><span data-stu-id="b434b-179">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="b434b-180">Podobně jako u částečných tříd může částečná metoda povolit kód vytvořený generátorem kódu a kódem vytvořeným vývojářem pro lidskou spolupráci bez nákladů na spuštění.</span><span class="sxs-lookup"><span data-stu-id="b434b-180">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="b434b-181">Deklarace částečné metody se skládá ze dvou částí: definice a implementace.</span><span class="sxs-lookup"><span data-stu-id="b434b-181">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="b434b-182">Ty mohou být v samostatných částech částečné třídy nebo ve stejné části.</span><span class="sxs-lookup"><span data-stu-id="b434b-182">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="b434b-183">Pokud není k dispozici žádná deklarace implementace, kompilátor optimalizuje jak definiční deklaraci, tak všechna volání metody.</span><span class="sxs-lookup"><span data-stu-id="b434b-183">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="b434b-184">Deklarace částečné metody musí začínat [částečným](../../language-reference/keywords/partial-type.md) klíčovým slovem kontextové a metoda musí vracet [typ void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="b434b-184">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="b434b-185">Částečné metody mohou mít [v](../../language-reference/keywords/in-parameter-modifier.md) parametrech nebo [ref](../../language-reference/keywords/ref.md) , ale ne [výstupní](../../language-reference/keywords/out-parameter-modifier.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="b434b-185">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="b434b-186">Částečné metody jsou implicitně [soukromé](../../language-reference/keywords/private.md), a proto nemohou být [virtuální](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="b434b-186">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="b434b-187">Částečné metody nemůžou být [extern](../../language-reference/keywords/extern.md), protože přítomnost těla určuje, jestli se definuje nebo implementuje.</span><span class="sxs-lookup"><span data-stu-id="b434b-187">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="b434b-188">Částečné metody mohou mít [statické](../../language-reference/keywords/static.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="b434b-188">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="b434b-189">Částečné metody mohou být obecné.</span><span class="sxs-lookup"><span data-stu-id="b434b-189">Partial methods can be generic.</span></span> <span data-ttu-id="b434b-190">Omezení jsou uvedena v deklaraci částečné deklarace metody a mohou být volitelně opakována při implementaci jednoho z nich.</span><span class="sxs-lookup"><span data-stu-id="b434b-190">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="b434b-191">Parametry a názvy parametrů typu nemusí být stejné v implementaci deklarace jako v rámci definujícího.</span><span class="sxs-lookup"><span data-stu-id="b434b-191">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="b434b-192">Můžete vytvořit [delegáta](../../language-reference/builtin-types/reference-types.md) částečné metody, která je definována a implementována, ale nikoli částečnou metodu, která byla definována pouze.</span><span class="sxs-lookup"><span data-stu-id="b434b-192">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b434b-193">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b434b-193">C# Language Specification</span></span>

<span data-ttu-id="b434b-194">Další informace naleznete v tématu [částečné typy](~/_csharplang/spec/classes.md#partial-types) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b434b-194">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b434b-195">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b434b-195">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b434b-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="b434b-196">See also</span></span>

- [<span data-ttu-id="b434b-197">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b434b-197">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b434b-198">Třídy</span><span class="sxs-lookup"><span data-stu-id="b434b-198">Classes</span></span>](./classes.md)
- [<span data-ttu-id="b434b-199">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="b434b-199">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="b434b-200">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b434b-200">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="b434b-201">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="b434b-201">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
