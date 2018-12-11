---
title: Částečné třídy a metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 222a47989537f09fd78c4a3b17fa8c1a5478d73f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243462"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="dc5e6-102">Částečné třídy a metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dc5e6-102">Partial Classes and Methods (C# Programming Guide)</span></span>
<span data-ttu-id="dc5e6-103">Je možné rozdělit definici [třídy](../../../csharp/language-reference/keywords/class.md), [struktura](../../../csharp/language-reference/keywords/struct.md), [rozhraní](../../../csharp/language-reference/keywords/interface.md) nebo metoda přes dvě nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-103">It is possible to split the definition of a [class](../../../csharp/language-reference/keywords/class.md), a [struct](../../../csharp/language-reference/keywords/struct.md), an [interface](../../../csharp/language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="dc5e6-104">Každý zdrojový soubor obsahuje část definice typu nebo metodě a všechny části spolu při kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-104">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>  
  
## <a name="partial-classes"></a><span data-ttu-id="dc5e6-105">Částečné třídy</span><span class="sxs-lookup"><span data-stu-id="dc5e6-105">Partial Classes</span></span>  
 <span data-ttu-id="dc5e6-106">Při rozdělování definici třídy je žádoucí, existuje několik situací:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-106">There are several situations when splitting a class definition is desirable:</span></span>  
  
-   <span data-ttu-id="dc5e6-107">Při práci na velkých projektech, rozdělit třídu samostatné soubory umožňuje více programátorům s ní pracují ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-107">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>  
  
-   <span data-ttu-id="dc5e6-108">Při práci se automaticky generovaná zdrojem, lze přidat kód do třídy bez nutnosti opětovného vytváření zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-108">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="dc5e6-109">Visual Studio používá tento přístup při vytváření formulářů Windows, obálky kódu webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-109">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="dc5e6-110">Můžete vytvořit kód, který používá tyto třídy, aniž byste museli upravovat soubor vytvořený pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-110">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>  
  
-   <span data-ttu-id="dc5e6-111">Pro rozdělení definice třídy, použijte [částečné](../../../csharp/language-reference/keywords/partial-type.md) – klíčové slovo modifikátoru, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-111">To split a class definition, use the [partial](../../../csharp/language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 <span data-ttu-id="dc5e6-112">`partial` – Klíčové slovo Určuje další části třídy, struktury nebo rozhraní lze definovat v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-112">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="dc5e6-113">Musíte použít všechny části `partial` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-113">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="dc5e6-114">Všechno, co musí být k dispozici v části doby kompilace a finální typu formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-114">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="dc5e6-115">Všechny součásti musí mít stejné usnadnění, například `public`, `private`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-115">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>  
  
 <span data-ttu-id="dc5e6-116">Pokud některá část je deklarováno jako abstraktní, pak celý typ je považován za abstraktní.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-116">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="dc5e6-117">Pokud některá část je deklarován zapečetěné, pak celý typ je považován za zapečetěná.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-117">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="dc5e6-118">Pokud některá část deklaruje základní typ, dědí celý typ třídy.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-118">If any part declares a base type, then the whole type inherits that class.</span></span>  
  
 <span data-ttu-id="dc5e6-119">Všechny součásti, které určují základní třída musí souhlasit, ale části, které vynechat základní třída dědí stále základního typu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-119">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="dc5e6-120">Části můžete zadat různé základní rozhraní a poslední typ implementuje všechna rozhraní, které jsou seřazené podle částečné deklarace.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-120">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="dc5e6-121">Všechny třídy, struktury nebo rozhraní členy deklarované v definici dílčí jsou k dispozici pro všechny ostatní součásti.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-121">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="dc5e6-122">Poslední typ je kombinací všech částí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-122">The final type is the combination of all the parts at compile time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5e6-123">`partial` Modifikátor není k dispozici v deklaracích delegáta nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-123">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>  
  
 <span data-ttu-id="dc5e6-124">Následující příklad ukazuje, že vnořené typy může být částečně, i když není typu, které jsou vnořené uvnitř částečné samotný.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-124">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 <span data-ttu-id="dc5e6-125">V době kompilace jsou sloučeny atributy částečný typ definice.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-125">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="dc5e6-126">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-126">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 <span data-ttu-id="dc5e6-127">Jsou ekvivalentní následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-127">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 <span data-ttu-id="dc5e6-128">Tyto jsou sloučeny ze všech definic částečného typu:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-128">The following are merged from all the partial-type definitions:</span></span>  
  
-   <span data-ttu-id="dc5e6-129">XML – komentáře</span><span class="sxs-lookup"><span data-stu-id="dc5e6-129">XML comments</span></span>  
  
-   <span data-ttu-id="dc5e6-130">rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc5e6-130">interfaces</span></span>  
  
-   <span data-ttu-id="dc5e6-131">atributy parametru obecného typu</span><span class="sxs-lookup"><span data-stu-id="dc5e6-131">generic-type parameter attributes</span></span>  
  
-   <span data-ttu-id="dc5e6-132">class – atributy</span><span class="sxs-lookup"><span data-stu-id="dc5e6-132">class attributes</span></span>  
  
-   <span data-ttu-id="dc5e6-133">členové</span><span class="sxs-lookup"><span data-stu-id="dc5e6-133">members</span></span>  
  
 <span data-ttu-id="dc5e6-134">Zvažte například následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-134">For example, consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 <span data-ttu-id="dc5e6-135">Jsou ekvivalentní následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-135">They are equivalent to the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a><span data-ttu-id="dc5e6-136">Omezení</span><span class="sxs-lookup"><span data-stu-id="dc5e6-136">Restrictions</span></span>  
 <span data-ttu-id="dc5e6-137">Existuje několik pravidel dodržovat při práci s definicí částečné třídy:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-137">There are several rules to follow when you are working with partial class definitions:</span></span>  
  
-   <span data-ttu-id="dc5e6-138">Všechny definice částečný typ má být součástí stejného typu musí být upravena se `partial`.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-138">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="dc5e6-139">Například následující deklarace třídy vygenerují chybu:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-139">For example, the following class declarations generate an error:</span></span>  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   <span data-ttu-id="dc5e6-140">`partial` Modifikátor se může objevit jenom bezprostředně před klíčová slova `class`, `struct`, nebo `interface`.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-140">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>  
  
-   <span data-ttu-id="dc5e6-141">Vnořené částečné typy jsou povoleny v definicích typu částečně, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-141">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   <span data-ttu-id="dc5e6-142">Všechny definice částečný typ má být součástí stejného typu musí být definován ve stejné sestavení a stejném modulu (soubor .exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="dc5e6-142">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="dc5e6-143">Částečné definice nemůžou zahrnovat více modulů.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-143">Partial definitions cannot span multiple modules.</span></span>  
  
-   <span data-ttu-id="dc5e6-144">Název třídy a parametry obecného typu musí odpovídat na všechny definice typu části.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-144">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="dc5e6-145">Obecné typy mohou být neúplná.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-145">Generic types can be partial.</span></span> <span data-ttu-id="dc5e6-146">Každý částečná deklarace musí používat stejné názvy parametrů ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-146">Each partial declaration must use the same parameter names in the same order.</span></span>  
  
-   <span data-ttu-id="dc5e6-147">Následující klíčová slova v definici typu částečné jsou volitelné, ale pokud jsou k dispozici na jednu definici částečného typu, nemohou kolidovat s klíčovými slovy zadaný v jiné částečné deklaraci pro stejného typu:</span><span class="sxs-lookup"><span data-stu-id="dc5e6-147">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>  
  
    -   [<span data-ttu-id="dc5e6-148">public</span><span class="sxs-lookup"><span data-stu-id="dc5e6-148">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
    -   [<span data-ttu-id="dc5e6-149">private</span><span class="sxs-lookup"><span data-stu-id="dc5e6-149">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
    -   [<span data-ttu-id="dc5e6-150">protected</span><span class="sxs-lookup"><span data-stu-id="dc5e6-150">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [<span data-ttu-id="dc5e6-151">internal</span><span class="sxs-lookup"><span data-stu-id="dc5e6-151">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [<span data-ttu-id="dc5e6-152">abstract</span><span class="sxs-lookup"><span data-stu-id="dc5e6-152">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [<span data-ttu-id="dc5e6-153">sealed</span><span class="sxs-lookup"><span data-stu-id="dc5e6-153">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   <span data-ttu-id="dc5e6-154">base – třída</span><span class="sxs-lookup"><span data-stu-id="dc5e6-154">base class</span></span>  
  
    -   <span data-ttu-id="dc5e6-155">[nové](../../../csharp/language-reference/keywords/new.md) modifikátor (vnořené částí)</span><span class="sxs-lookup"><span data-stu-id="dc5e6-155">[new](../../../csharp/language-reference/keywords/new.md) modifier (nested parts)</span></span>  
  
    -   <span data-ttu-id="dc5e6-156">Obecná omezení</span><span class="sxs-lookup"><span data-stu-id="dc5e6-156">generic constraints</span></span>  
  
         <span data-ttu-id="dc5e6-157">Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="dc5e6-157">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="dc5e6-158">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="dc5e6-158">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="dc5e6-159">Popis</span><span class="sxs-lookup"><span data-stu-id="dc5e6-159">Description</span></span>  
 <span data-ttu-id="dc5e6-160">V následujícím příkladu, polí a konstruktor třídy `CoOrds`, jsou deklarovány v jedné definici částečné třídy a člena, `PrintCoOrds`, je deklarována v jiné definici částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-160">In the following example, the fields and the constructor of the class, `CoOrds`, are declared in one partial class definition, and the member, `PrintCoOrds`, is declared in another partial class definition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dc5e6-161">Kód</span><span class="sxs-lookup"><span data-stu-id="dc5e6-161">Code</span></span>  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="dc5e6-162">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="dc5e6-162">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="dc5e6-163">Popis</span><span class="sxs-lookup"><span data-stu-id="dc5e6-163">Description</span></span>  
 <span data-ttu-id="dc5e6-164">Následující příklad ukazuje, že můžete také vyvíjet částečné struktury a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-164">The following example shows that you can also develop partial structs and interfaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dc5e6-165">Kód</span><span class="sxs-lookup"><span data-stu-id="dc5e6-165">Code</span></span>  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a><span data-ttu-id="dc5e6-166">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="dc5e6-166">Partial Methods</span></span>  
 <span data-ttu-id="dc5e6-167">Částečné třídy nebo struktury může obsahovat částečná metoda.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-167">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="dc5e6-168">Jednou ze součástí sady třídy obsahuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-168">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="dc5e6-169">Volitelné implementace může být definovaná v části stejné nebo jiné části.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-169">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="dc5e6-170">Pokud implementace není zadán, pak metoda a všechna volání do metody se odeberou v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-170">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>  
  
 <span data-ttu-id="dc5e6-171">Částečné metody umožňují implementátorovi jedné části třídy definují metody, podobné události.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-171">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="dc5e6-172">Implementátor druhou část třídy můžete rozhodnout, jestli se má implementovat metodu, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-172">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="dc5e6-173">Pokud metoda není implementována, pak kompilátor odebere metodu podpis a všechna volání do metody.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-173">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="dc5e6-174">Volání metody, včetně žádné výsledky, které by tomu bylo ze zkušební verze argumentů ve volání, nemají žádný vliv za běhu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-174">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="dc5e6-175">Proto žádný kód v dílčí třídě mohou volně používat částečné metody i v případě, že implementace není součástí.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-175">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="dc5e6-176">Žádné chyby kompilace nebo runtime dojde, pokud je metoda volána, ale není implementováno.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-176">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>  
  
 <span data-ttu-id="dc5e6-177">Částečné metody jsou zvláště užitečné jako způsob, jak přizpůsobit generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-177">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="dc5e6-178">Povolit pro název metody a podpis, které budou rezervovány, tak, že generovaný kód lze volat metodu, ale vývojář můžete rozhodnout, jestli se má implementovat metodu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-178">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="dc5e6-179">Podobně jako částečné třídy částečné metody umožňují kód vytvořený pomocí generátoru kódu a kód vytvořený vývojářem lidské spolupracovat bez nákladů za běhu.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-179">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>  
  
 <span data-ttu-id="dc5e6-180">Deklarace částečné metody se skládá ze dvou částí: definice a implementaci.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-180">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="dc5e6-181">Může to být v samostatné části částečné třídy nebo ve stejné části.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-181">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="dc5e6-182">Pokud neexistuje žádná deklarace implementace, pak kompilátor optimalizuje okamžitě obou definování prohlášení a všechna volání do metody.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-182">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   <span data-ttu-id="dc5e6-183">Deklarace částečné metody musí začínat kontextové klíčové slovo [částečné](../../../csharp/language-reference/keywords/partial-type.md) a metoda musí vracet [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="dc5e6-183">Partial method declarations must begin with the contextual keyword [partial](../../../csharp/language-reference/keywords/partial-type.md) and the method must return [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
-   <span data-ttu-id="dc5e6-184">Částečné metody mohou mít [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) , ale ne [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-184">Partial methods can have [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) but not [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
-   <span data-ttu-id="dc5e6-185">Částečné metody jsou implicitně [privátní](../../../csharp/language-reference/keywords/private.md), a proto nemůže být [virtuální](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="dc5e6-185">Partial methods are implicitly [private](../../../csharp/language-reference/keywords/private.md), and therefore they cannot be [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="dc5e6-186">Částečné metody nemohou být [extern](../../../csharp/language-reference/keywords/extern.md), protože existenci textu určuje, zda jejich definování nebo implementace.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-186">Partial methods cannot be [extern](../../../csharp/language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>  
  
-   <span data-ttu-id="dc5e6-187">Částečné metody mohou mít [statické](../../../csharp/language-reference/keywords/static.md) a [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-187">Partial methods can have [static](../../../csharp/language-reference/keywords/static.md) and [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifiers.</span></span>  
  
-   <span data-ttu-id="dc5e6-188">Částečné metody může být obecný.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-188">Partial methods can be generic.</span></span> <span data-ttu-id="dc5e6-189">Omezení se použijí na definující deklarace částečné metody a může volitelně opakována na implementující jeden.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-189">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="dc5e6-190">Názvy parametrů a typ parametrů není potřeba, aby měly stejnou v implementující deklarace, jako je definování.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-190">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>  
  
-   <span data-ttu-id="dc5e6-191">Můžete provést [delegovat](../../../csharp/language-reference/keywords/delegate.md) částečné metody, která byla definována a implementována, ale ne k částečné metody, která obsahuje jenom definice.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-191">You can make a [delegate](../../../csharp/language-reference/keywords/delegate.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc5e6-192">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc5e6-192">C# Language Specification</span></span>  

<span data-ttu-id="dc5e6-193">Další informace najdete v tématu [částečné typy](~/_csharplang/spec/classes.md#partial-types) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc5e6-193">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="dc5e6-194">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="dc5e6-194">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc5e6-195">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc5e6-195">See Also</span></span>

- [<span data-ttu-id="dc5e6-196">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dc5e6-196">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dc5e6-197">Třídy</span><span class="sxs-lookup"><span data-stu-id="dc5e6-197">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [<span data-ttu-id="dc5e6-198">Struktury</span><span class="sxs-lookup"><span data-stu-id="dc5e6-198">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [<span data-ttu-id="dc5e6-199">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc5e6-199">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="dc5e6-200">partial (typ)</span><span class="sxs-lookup"><span data-stu-id="dc5e6-200">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
