---
title: Metody (F#)
description: 'Zjistěte, jak metoda F # je přidružený k typu, které se používají k vystavení a implementaci funkce a chování objektů a typy funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: 02d5a7d22d1ce79a06e15462637c373b33623f61
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44253205"
---
# <a name="methods"></a><span data-ttu-id="89bcc-103">Metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-103">Methods</span></span>

<span data-ttu-id="89bcc-104">A *metoda* je funkce, který je přidružený k typu.</span><span class="sxs-lookup"><span data-stu-id="89bcc-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="89bcc-105">V objektově orientované programování metody se používají k vystavení a implementaci funkce a chování objektů a typy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="89bcc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89bcc-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="89bcc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89bcc-107">Remarks</span></span>

<span data-ttu-id="89bcc-108">V předchozí syntaxi zobrazí se různé formy metoda deklarace a definice.</span><span class="sxs-lookup"><span data-stu-id="89bcc-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="89bcc-109">V delší těl metod zalomení řádku následuje rovnítko (=) a tělo metody celý odsazena.</span><span class="sxs-lookup"><span data-stu-id="89bcc-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="89bcc-110">Atributy lze použít pro všechny deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="89bcc-111">Tyto předcházet syntaxe pro definici metody a obvykle jsou uvedeny na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="89bcc-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="89bcc-112">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="89bcc-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="89bcc-113">Metody mohou být označeny `inline`.</span><span class="sxs-lookup"><span data-stu-id="89bcc-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="89bcc-114">Informace o `inline`, naleznete v tématu [vložené funkce](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="89bcc-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="89bcc-115">Non-inline metod může být použité rekurzivně v rámci typu; není nutné explicitně `rec` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="89bcc-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="89bcc-116">Instance metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-116">Instance Methods</span></span>

<span data-ttu-id="89bcc-117">Instance metody jsou deklarovány pomocí `member` – klíčové slovo a *vlastní identifikátor*, následované tečkou (.) a název metody a parametrů.</span><span class="sxs-lookup"><span data-stu-id="89bcc-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="89bcc-118">Stejně jako v případě pro `let` vazeb *seznam parametrů* může být vzoru.</span><span class="sxs-lookup"><span data-stu-id="89bcc-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="89bcc-119">Obvykle použijte metodu, kterou parametry v závorkách v podobě řazené kolekce členů, což je způsob, jak metody se zobrazí v jazyce F # při jejich vytváření v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89bcc-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="89bcc-120">Ale curryfikované formuláře (parametry oddělené mezerami) je také obvyklé a dalších vzorech jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="89bcc-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="89bcc-121">Následující příklad ukazuje definici a využívání instance neabstraktní metoda.</span><span class="sxs-lookup"><span data-stu-id="89bcc-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="89bcc-122">V rámci metody instance nepoužívejte k přístupu pole definovaná pomocí vazby let identifikátoru samotného.</span><span class="sxs-lookup"><span data-stu-id="89bcc-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="89bcc-123">Při přístupu k ostatním členům a vlastnosti, použijte vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="89bcc-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="89bcc-124">Statické metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-124">Static Methods</span></span>

<span data-ttu-id="89bcc-125">Klíčové slovo `static` slouží k určení, že metodu lze volat bez instance a není přidružen k instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="89bcc-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="89bcc-126">V opačném případě metody jsou metody instance.</span><span class="sxs-lookup"><span data-stu-id="89bcc-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="89bcc-127">V příkladu v následující části zobrazuje pole deklarovaná s `let` – klíčové slovo, vlastnost členy deklarované s `member` – klíčové slovo a statické metody deklarované s `static` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="89bcc-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="89bcc-128">Následující příklad ukazuje definici a použití statické metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="89bcc-129">Předpokládejme, že jsou tyto definice metod v `SomeType` třídy v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="89bcc-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="89bcc-130">Abstraktní a virtuální metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="89bcc-131">Klíčové slovo `abstract` označuje, že metoda má virtuální odeslání slot a nemusí obsahovat definici třídy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="89bcc-132">A *virtuální odeslání slotu* je záznam v tabulce vnitřně udržované funkcí, který se používá v době běhu k vyhledání virtuální funkce se volá v typu objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="89bcc-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="89bcc-133">Mechanismus virtuální odeslání je mechanismus, který implementuje *polymorfismus*, důležitou funkcí objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="89bcc-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="89bcc-134">Je třída, která má alespoň jeden abstraktní metody bez definice *abstraktní třída*, což znamená, že nemohou být vytvořeny žádné instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="89bcc-135">Další informace o abstraktních tříd naleznete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="89bcc-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="89bcc-136">Deklarace abstraktní metody nezahrnují tělo metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="89bcc-137">Název metody je místo, následovaný dvojtečkou (:) a podpis typu metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="89bcc-138">Podpis typu metody je stejný jako uvedeny technologií IntelliSense při pozastavení ukazatele myši nad název metody v editoru Visual Studio Code, s výjimkou bez názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="89bcc-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="89bcc-139">Typ signatury jsou také zobrazí interpret, fsi.exe, když interaktivně pracovat.</span><span class="sxs-lookup"><span data-stu-id="89bcc-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="89bcc-140">Podpis typu metody je tvořen přidáním výpis na typy parametrů, za nímž následuje návratový typ se symboly příslušné oddělovače.</span><span class="sxs-lookup"><span data-stu-id="89bcc-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="89bcc-141">Curryfikované parametrů je odděleno `->` a parametry řazené kolekce členů jsou odděleny `*`.</span><span class="sxs-lookup"><span data-stu-id="89bcc-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="89bcc-142">Vrácená hodnota je vždy oddělená od argumenty podle `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="89bcc-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="89bcc-143">Závorky lze použít k seskupení složité parametry, například když typ funkce je parametr, nebo k označení, když řazené kolekce členů je zpracováván jako jediný parametr, nikoli jako dva parametry.</span><span class="sxs-lookup"><span data-stu-id="89bcc-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="89bcc-144">Můžete také udělit abstraktní metody výchozí definice přidání definice třídy a použitím `default` – klíčové slovo, jak je znázorněno v syntaxi bloku v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="89bcc-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="89bcc-145">Abstraktní metody, která má definici ve stejné třídě, je ekvivalentní virtuální metody v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89bcc-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="89bcc-146">Určuje, jestli existuje definice, `abstract` – klíčové slovo vytvoří nový slot odbavení v tabulce virtuální funkce třídy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="89bcc-147">Bez ohledu na to, zda základní třída implementuje abstraktní metody mohou odvozené třídy poskytují implementace abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="89bcc-148">Chcete-li implementovat abstraktní metoda v odvozené třídě, definujte metodu, která má stejný název a signaturu v odvozené třídě, s výjimkou použití `override` nebo `default` – klíčové slovo a poskytnout tělo metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="89bcc-149">Klíčová slova `override` a `default` přesně stejný význam.</span><span class="sxs-lookup"><span data-stu-id="89bcc-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="89bcc-150">Použít `override` Pokud přepisuje nová metoda implementaci základní třídy; použijte `default` při vytváření implementaci ve třídě stejný jako původní deklarace abstraktní.</span><span class="sxs-lookup"><span data-stu-id="89bcc-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="89bcc-151">Nepoužívejte `abstract` – klíčové slovo v metodě, která implementuje metodu, která byla deklarovaná jako abstraktní základní třídy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="89bcc-152">Následující příklad ukazuje abstraktní metody `Rotate` , který má výchozí implementaci ekvivalent virtuální metody rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89bcc-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="89bcc-153">Následující příklad ukazuje odvozené třídy, která přepíše metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="89bcc-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="89bcc-154">V takovém případě přepsání mění chování tak, aby metoda nemá žádný účinek.</span><span class="sxs-lookup"><span data-stu-id="89bcc-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="89bcc-155">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-155">Overloaded Methods</span></span>

<span data-ttu-id="89bcc-156">Přetížené metody jsou metody, které mají stejný název v daného typu, ale mají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="89bcc-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="89bcc-157">V jazyce F # jsou volitelné argumenty obvykle používají místo přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="89bcc-158">Ale přetížené metody jsou povoleny v jazyce, za předpokladu, že jsou argumenty v podobě řazené kolekce členů, není curryfikované formuláře.</span><span class="sxs-lookup"><span data-stu-id="89bcc-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="89bcc-159">Nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="89bcc-159">Optional Arguments</span></span>

<span data-ttu-id="89bcc-160">Od verze F # 4.1, můžete mít také volitelné argumenty s výchozí hodnotou parametru do metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="89bcc-161">Toto je usnadňují spolupráci s kódem C#.</span><span class="sxs-lookup"><span data-stu-id="89bcc-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="89bcc-162">Následující příklad ukazuje syntaxi:</span><span class="sxs-lookup"><span data-stu-id="89bcc-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="89bcc-163">Všimněte si, že hodnota předaná pro `DefaultParameterValue` musí shodovat s typem vstupu.</span><span class="sxs-lookup"><span data-stu-id="89bcc-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="89bcc-164">V ukázce výše, je `int`.</span><span class="sxs-lookup"><span data-stu-id="89bcc-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="89bcc-165">Pokus o předání hodnot jiných než celých čísel do `DefaultParameterValue` způsobí chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="89bcc-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="89bcc-166">Příklad: Vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="89bcc-166">Example: Properties and Methods</span></span>

<span data-ttu-id="89bcc-167">Následující příklad obsahuje typ, který obsahuje příklady polí, soukromé funkce, vlastnosti a statické metody.</span><span class="sxs-lookup"><span data-stu-id="89bcc-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="89bcc-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89bcc-168">See also</span></span>

- [<span data-ttu-id="89bcc-169">Členové</span><span class="sxs-lookup"><span data-stu-id="89bcc-169">Members</span></span>](index.md)
