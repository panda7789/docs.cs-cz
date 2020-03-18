---
title: Částečné třídy a metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399817"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="ce578-102">Částečné třídy a metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ce578-102">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="ce578-103">Je možné rozdělit definici [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md), [rozhraní](../../language-reference/keywords/interface.md) nebo metody na dva nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="ce578-103">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="ce578-104">Každý zdrojový soubor obsahuje část definice typu nebo metody a všechny části jsou kombinovány při kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce578-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="ce578-105">Částečné třídy</span><span class="sxs-lookup"><span data-stu-id="ce578-105">Partial Classes</span></span>

<span data-ttu-id="ce578-106">Existuje několik situací, kdy je žádoucí rozdělení definice třídy:</span><span class="sxs-lookup"><span data-stu-id="ce578-106">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="ce578-107">Při práci na velkých projektech umožňuje rozprostření třídy přes samostatné soubory více programátorům pracovat na ní současně.</span><span class="sxs-lookup"><span data-stu-id="ce578-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="ce578-108">Při práci s automaticky generovaným zdrojem lze kód přidat do třídy bez nutnosti znovu vytvořit zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="ce578-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="ce578-109">Visual Studio používá tento přístup při vytváření formulářů Windows, obálkový kód webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ce578-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="ce578-110">Můžete vytvořit kód, který používá tyto třídy bez nutnosti upravovat soubor vytvořený visual studio.</span><span class="sxs-lookup"><span data-stu-id="ce578-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="ce578-111">Chcete-li rozdělit definici třídy, použijte modifikátor [částečného](../../language-reference/keywords/partial-type.md) klíčového slova, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="ce578-111">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

<span data-ttu-id="ce578-112">Klíčové `partial` slovo označuje, že ostatní části třídy, struktury nebo rozhraní mohou být definovány v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ce578-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="ce578-113">Všechny části musí `partial` používat klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ce578-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="ce578-114">Všechny části musí být k dispozici v době kompilace tvořit konečný typ.</span><span class="sxs-lookup"><span data-stu-id="ce578-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="ce578-115">Všechny součásti musí mít stejnou `public`přístupnost, například , `private`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ce578-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="ce578-116">Pokud je kterákoli část deklarována jako abstraktní, je celý typ považován za abstraktní.</span><span class="sxs-lookup"><span data-stu-id="ce578-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="ce578-117">Pokud je některá část prohlášena za uzavřenou, považuje se celý typ za zapečetěný.</span><span class="sxs-lookup"><span data-stu-id="ce578-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="ce578-118">Pokud některá část deklaruje základní typ, pak celý typ dědí tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="ce578-118">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="ce578-119">Všechny části, které určují základní třídu, musí souhlasit, ale části, které vynechou základní třídu, stále dědí základní typ.</span><span class="sxs-lookup"><span data-stu-id="ce578-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="ce578-120">Části můžete určit různé základní rozhraní a konečný typ implementuje všechna rozhraní uvedená ve všech částečných deklaracích.</span><span class="sxs-lookup"><span data-stu-id="ce578-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="ce578-121">Všechny členy třídy, struktury nebo rozhraní deklarované v částečné definici jsou k dispozici pro všechny ostatní části.</span><span class="sxs-lookup"><span data-stu-id="ce578-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="ce578-122">Konečný typ je kombinací všech částí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="ce578-122">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="ce578-123">Modifikátor `partial` není k dispozici v deklaracích delegáta nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="ce578-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="ce578-124">Následující příklad ukazuje, že vnořené typy mohou být částečné, i když typ, ve které jsou vnořené, není částečný sám.</span><span class="sxs-lookup"><span data-stu-id="ce578-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

<span data-ttu-id="ce578-125">V době kompilace jsou sloučeny atributy definice částečného typu.</span><span class="sxs-lookup"><span data-stu-id="ce578-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="ce578-126">Zvažte například následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="ce578-126">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

<span data-ttu-id="ce578-127">Jsou rovnocenné následujícím prohlášením:</span><span class="sxs-lookup"><span data-stu-id="ce578-127">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

<span data-ttu-id="ce578-128">Následující jsou sloučeny ze všech definic částečného typu:</span><span class="sxs-lookup"><span data-stu-id="ce578-128">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="ce578-129">XML – komentáře</span><span class="sxs-lookup"><span data-stu-id="ce578-129">XML comments</span></span>

- <span data-ttu-id="ce578-130">rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce578-130">interfaces</span></span>

- <span data-ttu-id="ce578-131">atributy parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="ce578-131">generic-type parameter attributes</span></span>

- <span data-ttu-id="ce578-132">class – atributy</span><span class="sxs-lookup"><span data-stu-id="ce578-132">class attributes</span></span>

- <span data-ttu-id="ce578-133">členy</span><span class="sxs-lookup"><span data-stu-id="ce578-133">members</span></span>

<span data-ttu-id="ce578-134">Zvažte například následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="ce578-134">For example, consider the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

<span data-ttu-id="ce578-135">Jsou rovnocenné následujícím prohlášením:</span><span class="sxs-lookup"><span data-stu-id="ce578-135">They are equivalent to the following declarations:</span></span>

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a><span data-ttu-id="ce578-136">Omezení</span><span class="sxs-lookup"><span data-stu-id="ce578-136">Restrictions</span></span>

<span data-ttu-id="ce578-137">Při práci s částečnými definicemi tříd je třeba dodržovat několik pravidel:</span><span class="sxs-lookup"><span data-stu-id="ce578-137">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="ce578-138">Všechny definice částečného typu, které mají být součástí `partial`stejného typu, musí být změněny pomocí .</span><span class="sxs-lookup"><span data-stu-id="ce578-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="ce578-139">Například následující deklarace třídy generují chybu:</span><span class="sxs-lookup"><span data-stu-id="ce578-139">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- <span data-ttu-id="ce578-140">`partial` Modifikátor se může objevit `class`pouze `struct`bezprostředně `interface`před klíčovými slovy , nebo .</span><span class="sxs-lookup"><span data-stu-id="ce578-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="ce578-141">Vnořené částečné typy jsou povoleny v definicích částečného typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ce578-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- <span data-ttu-id="ce578-142">Všechny definice částečného typu, které mají být součástí stejného typu, musí být definovány ve stejném sestavení a ve stejném modulu (soubor .exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="ce578-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="ce578-143">Částečné definice nemohou mít více modulů.</span><span class="sxs-lookup"><span data-stu-id="ce578-143">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="ce578-144">Název třídy a parametry obecného typu musí odpovídat všem definicím částečného typu.</span><span class="sxs-lookup"><span data-stu-id="ce578-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="ce578-145">Obecné typy mohou být částečné.</span><span class="sxs-lookup"><span data-stu-id="ce578-145">Generic types can be partial.</span></span> <span data-ttu-id="ce578-146">Každá částečná deklarace musí používat stejné názvy parametrů ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ce578-146">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="ce578-147">Následující klíčová slova v definici částečného typu jsou nepovinná, ale pokud jsou k dispozici v jedné definici částečného typu, nemohou být v konfliktu s klíčovými slovy zadanými v jiné částečné definici pro stejný typ:</span><span class="sxs-lookup"><span data-stu-id="ce578-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="ce578-148">Veřejné</span><span class="sxs-lookup"><span data-stu-id="ce578-148">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="ce578-149">Soukromé</span><span class="sxs-lookup"><span data-stu-id="ce578-149">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="ce578-150">protected</span><span class="sxs-lookup"><span data-stu-id="ce578-150">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="ce578-151">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="ce578-151">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="ce578-152">Abstraktní</span><span class="sxs-lookup"><span data-stu-id="ce578-152">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="ce578-153">sealed</span><span class="sxs-lookup"><span data-stu-id="ce578-153">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="ce578-154">base – třída</span><span class="sxs-lookup"><span data-stu-id="ce578-154">base class</span></span>

  - <span data-ttu-id="ce578-155">[nový](../../language-reference/keywords/new-modifier.md) modifikátor (vnořené části)</span><span class="sxs-lookup"><span data-stu-id="ce578-155">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="ce578-156">obecná omezení</span><span class="sxs-lookup"><span data-stu-id="ce578-156">generic constraints</span></span>

<span data-ttu-id="ce578-157">Další informace naleznete [v tématu Omezení parametrů typu](../generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ce578-157">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="ce578-158">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="ce578-158">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="ce578-159">Popis</span><span class="sxs-lookup"><span data-stu-id="ce578-159">Description</span></span>

<span data-ttu-id="ce578-160">V následujícím příkladu jsou pole a konstruktor `Coords`třídy , deklarovány v `PrintCoords`jedné definici částečné třídy a člen , je deklarován v jiné definici částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="ce578-160">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="ce578-161">kód</span><span class="sxs-lookup"><span data-stu-id="ce578-161">Code</span></span>

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a><span data-ttu-id="ce578-162">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="ce578-162">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="ce578-163">Popis</span><span class="sxs-lookup"><span data-stu-id="ce578-163">Description</span></span>

<span data-ttu-id="ce578-164">Následující příklad ukazuje, že můžete také vyvinout částečné struktury a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ce578-164">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="ce578-165">kód</span><span class="sxs-lookup"><span data-stu-id="ce578-165">Code</span></span>

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a><span data-ttu-id="ce578-166">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="ce578-166">Partial Methods</span></span>

<span data-ttu-id="ce578-167">Částečná třída nebo struktura může obsahovat částečnou metodu.</span><span class="sxs-lookup"><span data-stu-id="ce578-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="ce578-168">Jedna část třídy obsahuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="ce578-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="ce578-169">Volitelná implementace může být definována ve stejné nebo jiné části.</span><span class="sxs-lookup"><span data-stu-id="ce578-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="ce578-170">Pokud implementace není zadána, pak metoda a všechna volání metody jsou odebrány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="ce578-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="ce578-171">Částečné metody umožňují implementátoru jedné části třídy definovat metodu, podobně jako událost.</span><span class="sxs-lookup"><span data-stu-id="ce578-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="ce578-172">Implementátor druhé části třídy se může rozhodnout, zda metodu implementovat či nikoli.</span><span class="sxs-lookup"><span data-stu-id="ce578-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="ce578-173">Pokud metoda není implementována, pak kompilátor odebere podpis metody a všechna volání metody.</span><span class="sxs-lookup"><span data-stu-id="ce578-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="ce578-174">Volání metody, včetně všech výsledků, které by nastaly z vyhodnocení argumentů v volání, nemají žádný vliv v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ce578-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="ce578-175">Proto jakýkoli kód v částečné třídě můžete volně používat částečnou metodu, i v případě, že implementace není zadána.</span><span class="sxs-lookup"><span data-stu-id="ce578-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="ce578-176">Žádné chyby kompilace nebo za běhu dojde, pokud je metoda volána, ale není implementována.</span><span class="sxs-lookup"><span data-stu-id="ce578-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="ce578-177">Částečné metody jsou užitečné zejména jako způsob přizpůsobení generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ce578-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="ce578-178">Umožňují název metody a podpis, které mají být vyhrazeny, tak, aby generovaný kód může volat metodu, ale vývojář se může rozhodnout, zda implementovat metodu.</span><span class="sxs-lookup"><span data-stu-id="ce578-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="ce578-179">Podobně jako částečné třídy, částečné metody umožňují kód vytvořený generátorem kódu a kód vytvořený lidským vývojářem pro spolupráci bez nákladů za běhu.</span><span class="sxs-lookup"><span data-stu-id="ce578-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="ce578-180">Deklarace částečné metody se skládá ze dvou částí: definice a implementace.</span><span class="sxs-lookup"><span data-stu-id="ce578-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="ce578-181">Ty mohou být v samostatných částech částečné třídy nebo ve stejné části.</span><span class="sxs-lookup"><span data-stu-id="ce578-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="ce578-182">Pokud neexistuje žádná deklarace implementace, pak kompilátor optimalizuje pryč definování deklarace a všechna volání metody.</span><span class="sxs-lookup"><span data-stu-id="ce578-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="ce578-183">Deklarace částečné metody musí začínat kontextovým klíčovým slovem [partial](../../language-reference/keywords/partial-type.md) a metoda musí vrátit [void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="ce578-183">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="ce578-184">Částečné metody mohou mít [v](../../language-reference/keywords/in-parameter-modifier.md) nebo [ref,](../../language-reference/keywords/ref.md) ale ne [out](../../language-reference/keywords/out-parameter-modifier.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="ce578-184">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="ce578-185">Částečné metody jsou implicitně [soukromé](../../language-reference/keywords/private.md), a proto nemohou být [virtuální](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="ce578-185">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="ce578-186">Částečné metody nemohou být [extern](../../language-reference/keywords/extern.md), protože přítomnost těla určuje, zda jsou definování nebo provádění.</span><span class="sxs-lookup"><span data-stu-id="ce578-186">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="ce578-187">Částečné metody mohou mít [statické](../../language-reference/keywords/static.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="ce578-187">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="ce578-188">Částečné metody mohou být obecné.</span><span class="sxs-lookup"><span data-stu-id="ce578-188">Partial methods can be generic.</span></span> <span data-ttu-id="ce578-189">Omezení jsou umístěny na definování deklarace částečné metody a může být volitelně opakovat na prováděcí jeden.</span><span class="sxs-lookup"><span data-stu-id="ce578-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="ce578-190">Názvy parametrů a parametrů typu nemusí být v prováděcí deklaraci stejné jako v definujícím prohlášení.</span><span class="sxs-lookup"><span data-stu-id="ce578-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="ce578-191">Můžete vytvořit [delegáta](../../language-reference/builtin-types/reference-types.md) na částečnou metodu, která byla definována a implementována, ale ne na částečnou metodu, která byla definována pouze.</span><span class="sxs-lookup"><span data-stu-id="ce578-191">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ce578-192">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce578-192">C# Language Specification</span></span>

<span data-ttu-id="ce578-193">Další informace naleznete v tématu [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="ce578-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ce578-194">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ce578-194">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce578-195">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce578-195">See also</span></span>

- [<span data-ttu-id="ce578-196">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce578-196">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce578-197">Třídy</span><span class="sxs-lookup"><span data-stu-id="ce578-197">Classes</span></span>](./classes.md)
- [<span data-ttu-id="ce578-198">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="ce578-198">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="ce578-199">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce578-199">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="ce578-200">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="ce578-200">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
