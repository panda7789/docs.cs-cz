---
title: "Částečné třídy a metody (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 662b3308c3baa429ed29adca750cbb9b143b79dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="baf96-102">Částečné třídy a metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="baf96-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="baf96-103">Je možné rozdělit definice [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), [rozhraní](../../../csharp/language-reference/keywords/interface.md) nebo metoda přes dvě nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="baf96-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="baf96-104">Každý zdrojový soubor obsahuje oddíl definice typ nebo metoda a všechny části spojují během kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="baf96-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="baf96-105">Částečné třídy</span><span class="sxs-lookup"><span data-stu-id="baf96-105">Partial Classes</span></span>  
 <span data-ttu-id="baf96-106">Při rozdělování definice třídy je žádoucí existuje několik situací:</span><span class="sxs-lookup"><span data-stu-id="baf96-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="baf96-107">Při práci na velkých projektech, šíří třídu po samostatné soubory umožňuje více programátorům práci ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="baf96-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="baf96-108">Při práci se zdrojem automaticky generované, kód můžete přidat do třídy bez nutnosti opětného vytváření zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="baf96-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="baf96-109">Visual Studio použije tento přístup při vytváření Windows Forms, kódu obálky webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="baf96-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="baf96-110">Můžete vytvořit kód, který používá tyto třídy, aniž by bylo nutné upravit soubor vytvořený pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="baf96-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="baf96-111">Rozdělení definice třídy, použijte [částečné](../../../csharp/language-reference/keywords/partial-type.md) – klíčové slovo modifikátoru, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="baf96-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 <span data-ttu-id="baf96-112">`partial` – Klíčové slovo označuje, že dalších částí třída, struktura, nebo rozhraní lze definovat v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="baf96-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="baf96-113">Musíte použít všechny části `partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="baf96-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="baf96-114">Všechny části musí být k dispozici v kompilaci čas poslední typ formuláře.</span><span class="sxs-lookup"><span data-stu-id="baf96-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="baf96-115">Všechny části musí mít stejné usnadnění jako `public`, `private`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="baf96-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="baf96-116">Libovolnou část je deklarovaná abstraktní, celý typ se považuje abstraktní.</span><span class="sxs-lookup"><span data-stu-id="baf96-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="baf96-117">Pokud některou část deklarována zapečetěné, pak celý typ je považován za zapečetěná.</span><span class="sxs-lookup"><span data-stu-id="baf96-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="baf96-118">Pokud některou část deklaruje základní typ, dědí celou typ třídy.</span><span class="sxs-lookup"><span data-stu-id="baf96-118">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="baf96-119">Všechny součásti, které zadejte základní třídu, musíte souhlasit, ale částí, které vynechejte základní třídu stále dědění základního typu.</span><span class="sxs-lookup"><span data-stu-id="baf96-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="baf96-120">Části můžete zadat různé základní rozhraní a typ konečné implementuje všechna rozhraní uvedené podle částečné deklarace.</span><span class="sxs-lookup"><span data-stu-id="baf96-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="baf96-121">Všechny třída, struktura nebo členové rozhraní, které jsou deklarované v definici částečné jsou k dispozici pro všechny ostatní části.</span><span class="sxs-lookup"><span data-stu-id="baf96-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="baf96-122">Poslední typ je kombinace všechny části v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="baf96-122">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baf96-123">`partial` Modifikátor není k dispozici v deklaracích delegáta nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="baf96-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="baf96-124">Následující příklad ukazuje, že vnořené typy mohou být částečné, i když není zadaný typ, že jsou vnořené do částečné sám sebe.</span><span class="sxs-lookup"><span data-stu-id="baf96-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 <span data-ttu-id="baf96-125">Při kompilaci jsou sloučeny atributy definicí partial-type.</span><span class="sxs-lookup"><span data-stu-id="baf96-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="baf96-126">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="baf96-126">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 <span data-ttu-id="baf96-127">Jsou ekvivalentní následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="baf96-127">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 <span data-ttu-id="baf96-128">Toto jsou slučovány z všech definic partial-type:</span><span class="sxs-lookup"><span data-stu-id="baf96-128">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="baf96-129">XML – komentáře</span><span class="sxs-lookup"><span data-stu-id="baf96-129">XML comments</span></span>  
  
-   <span data-ttu-id="baf96-130">rozhraní</span><span class="sxs-lookup"><span data-stu-id="baf96-130">interfaces</span></span>  
  
-   <span data-ttu-id="baf96-131">Parametr obecného typu atributy</span><span class="sxs-lookup"><span data-stu-id="baf96-131">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="baf96-132">class – atributy</span><span class="sxs-lookup"><span data-stu-id="baf96-132">class attributes</span></span>  
  
-   <span data-ttu-id="baf96-133">členy</span><span class="sxs-lookup"><span data-stu-id="baf96-133">members</span></span>  
  
 <span data-ttu-id="baf96-134">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="baf96-134">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 <span data-ttu-id="baf96-135">Jsou ekvivalentní následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="baf96-135">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a><span data-ttu-id="baf96-136">Omezení</span><span class="sxs-lookup"><span data-stu-id="baf96-136">Restrictions</span></span>  
 <span data-ttu-id="baf96-137">Existuje několik pravidla při práci se definice pro třídu:</span><span class="sxs-lookup"><span data-stu-id="baf96-137">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="baf96-138">Všechny definice typu partial určené jako součásti stejného typu musí být upravena se `partial`.</span><span class="sxs-lookup"><span data-stu-id="baf96-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="baf96-139">Například následující deklarace třídy vygenerovat chybu:</span><span class="sxs-lookup"><span data-stu-id="baf96-139">For example, the following class declarations generate an error:</span></span>  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   <span data-ttu-id="baf96-140">`partial` Modifikátoru může vyskytovat pouze bezprostředně před klíčová slova `class`, `struct`, nebo `interface`.</span><span class="sxs-lookup"><span data-stu-id="baf96-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="baf96-141">Vnořené částečné typy jsou povoleny v definicích partial-type, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="baf96-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   <span data-ttu-id="baf96-142">Všechny definice typu partial určené jako součásti stejného typu musí být definovaný ve stejném sestavení a stejné modul (soubor .exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="baf96-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="baf96-143">Částečné definice nemůžou zahrnovat více modulů.</span><span class="sxs-lookup"><span data-stu-id="baf96-143">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="baf96-144">Název třídy a parametry obecného typu musí odpovídat na všechny definice partial-type.</span><span class="sxs-lookup"><span data-stu-id="baf96-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="baf96-145">Obecné typy může být částečné.</span><span class="sxs-lookup"><span data-stu-id="baf96-145">Generic types can be partial.</span></span> <span data-ttu-id="baf96-146">Každá částečné deklarace, musíte použít stejné názvy parametrů ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="baf96-146">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="baf96-147">Následující klíčová slova v definici typu partial jsou nepovinné, ale pokud je k dispozici na jednu definici partial typu, nelze v konfliktu s klíčová slova v jiné definici částečné pro stejný typ zadaný:</span><span class="sxs-lookup"><span data-stu-id="baf96-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="baf96-148">veřejné</span><span class="sxs-lookup"><span data-stu-id="baf96-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="baf96-149">privátní</span><span class="sxs-lookup"><span data-stu-id="baf96-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="baf96-150">chráněný</span><span class="sxs-lookup"><span data-stu-id="baf96-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="baf96-151">interní</span><span class="sxs-lookup"><span data-stu-id="baf96-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="baf96-152">abstraktní</span><span class="sxs-lookup"><span data-stu-id="baf96-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="baf96-153">zapečetěná</span><span class="sxs-lookup"><span data-stu-id="baf96-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="baf96-154">base – třída</span><span class="sxs-lookup"><span data-stu-id="baf96-154">base class</span></span>  
  
    -   <span data-ttu-id="baf96-155">[nové](../../../csharp/language-reference/keywords/new.md) – modifikátor (vnořené částí)</span><span class="sxs-lookup"><span data-stu-id="baf96-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="baf96-156">Obecná omezení</span><span class="sxs-lookup"><span data-stu-id="baf96-156">generic constraints</span></span>  
  
         <span data-ttu-id="baf96-157">Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="baf96-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="baf96-158">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="baf96-158">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="baf96-159">Popis</span><span class="sxs-lookup"><span data-stu-id="baf96-159">Description</span></span>  
 <span data-ttu-id="baf96-160">V následujícím příkladu, pole a konstruktoru třídy `CoOrds`, jsou deklarované v jedné definice částečné třídy a člen, `PrintCoOrds`, je v jiné definici třídu deklarovat.</span><span class="sxs-lookup"><span data-stu-id="baf96-160">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="baf96-161">Kód</span><span class="sxs-lookup"><span data-stu-id="baf96-161">Code</span></span>  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="baf96-162">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="baf96-162">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="baf96-163">Popis</span><span class="sxs-lookup"><span data-stu-id="baf96-163">Description</span></span>  
 <span data-ttu-id="baf96-164">Následující příklad ukazuje, že můžete také vyvíjet částečné struktury a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="baf96-164">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="baf96-165">Kód</span><span class="sxs-lookup"><span data-stu-id="baf96-165">Code</span></span>  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a><span data-ttu-id="baf96-166">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="baf96-166">Partial Methods</span></span>  
 <span data-ttu-id="baf96-167">Částečné metody mohou obsahovat částečné třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="baf96-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="baf96-168">Jeden součástí třídy obsahuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="baf96-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="baf96-169">Volitelné implementace může být definovány v části stejné nebo jiné části.</span><span class="sxs-lookup"><span data-stu-id="baf96-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="baf96-170">Pokud je implementace není zadaný, poté metoda a všechna volání do metody odstraněny při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="baf96-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="baf96-171">Částečné metody povolit implementátor jednou ze součástí sady třídu definovat metodu, podobné události.</span><span class="sxs-lookup"><span data-stu-id="baf96-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="baf96-172">Implementátor na straně druhé třídy se můžete rozhodnout, zda implementovat metodu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="baf96-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="baf96-173">Pokud metoda není implementována, pak kompilátor odebere metodu podpisu a všechna volání do metody.</span><span class="sxs-lookup"><span data-stu-id="baf96-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="baf96-174">Volání metody, včetně všechny výsledky, které by tomu bylo ze zkušební verze argumentů ve voláních, nemají žádný vliv za běhu.</span><span class="sxs-lookup"><span data-stu-id="baf96-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="baf96-175">Proto žádný kód v třídu můžete volně použít částečné metodu, i v případě, že není součástí implementace.</span><span class="sxs-lookup"><span data-stu-id="baf96-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="baf96-176">Žádné chyby kompilace nebo běhu dojde, pokud metoda je volána, ale není implementováno.</span><span class="sxs-lookup"><span data-stu-id="baf96-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="baf96-177">Částečné metody jsou užitečné zejména jako způsob, jak přizpůsobit generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="baf96-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="baf96-178">Povolí pro název metody a podpis jako vyhrazené, tak, aby generovaného kódu můžete volat metodu ale vývojář může rozhodnout, zda chcete implementovat metodu.</span><span class="sxs-lookup"><span data-stu-id="baf96-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="baf96-179">Částečné třídy, jako je mnohem částečné metody povolit kód vytvořený generátor kódu a kód vytvořený vývojářem, který spolupracovat bez běhové náklady na lidské.</span><span class="sxs-lookup"><span data-stu-id="baf96-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="baf96-180">Deklarace částečné metody se skládá ze dvou částí: definice a implementaci.</span><span class="sxs-lookup"><span data-stu-id="baf96-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="baf96-181">To může být v samostatné části částečné třídy, nebo ve stejné části.</span><span class="sxs-lookup"><span data-stu-id="baf96-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="baf96-182">Pokud není k dispozici žádná deklarace implementace, pak kompilátor optimalizuje rychle i definování deklarace a všechna volání do metody.</span><span class="sxs-lookup"><span data-stu-id="baf96-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="baf96-183">Částečné metody deklarace musí začínat kontextové klíčové slovo [částečné](../../../csharp/language-reference/keywords/partial-type.md) a musí vracet metodu [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="baf96-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="baf96-184">Částečné metody může mít [ref](../../../csharp/language-reference/keywords/ref.md) ale ne [out](../../../csharp/language-reference/keywords/out.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="baf96-184">Partial methods can have [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out.md) parameters.</span></span>  
  
-   <span data-ttu-id="baf96-185">Částečné metody jsou implicitně [privátní](../../../csharp/language-reference/keywords/private.md), a proto nemůže být [virtuální](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="baf96-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="baf96-186">Částečné metody nemůže být [extern](../../../csharp/language-reference/keywords/extern.md), protože přítomnost text určuje, zda jsou definování nebo implementace.</span><span class="sxs-lookup"><span data-stu-id="baf96-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="baf96-187">Částečné metody může mít [statické](../../../csharp/language-reference/keywords/static.md) a [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="baf96-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="baf96-188">Částečné metody mohou být obecný.</span><span class="sxs-lookup"><span data-stu-id="baf96-188">Partial methods can be generic.</span></span> <span data-ttu-id="baf96-189">Omezení se umístí definující deklarace částečné metody a může volitelně opakována na implementující jeden.</span><span class="sxs-lookup"><span data-stu-id="baf96-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="baf96-190">Parametr a zadejte názvy parametrů nemusí být stejný v implementující deklaraci jako definující jeden.</span><span class="sxs-lookup"><span data-stu-id="baf96-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="baf96-191">Můžete provést [delegovat](../../../csharp/language-reference/keywords/delegate.md) částečné metodu, která byla definována a implementována, ale není částečné metodu, která pouze byla definována.</span><span class="sxs-lookup"><span data-stu-id="baf96-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="baf96-192">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="baf96-192">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="baf96-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="baf96-193">See Also</span></span>  
 [<span data-ttu-id="baf96-194">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="baf96-194">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="baf96-195">Třídy</span><span class="sxs-lookup"><span data-stu-id="baf96-195">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [<span data-ttu-id="baf96-196">Struktury</span><span class="sxs-lookup"><span data-stu-id="baf96-196">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="baf96-197">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="baf96-197">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="baf96-198">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="baf96-198">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
