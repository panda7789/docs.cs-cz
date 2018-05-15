---
title: Metody (F#)
description: 'Zjistěte, jak metodu F # je přidružený k typu, které se používají k vystavení a implementovat funkce a chování objekty a typy funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: 6e0b0789d97a9671425fb08c56c84ba1f66dfbe6
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2018
---
# <a name="methods"></a><span data-ttu-id="6dede-103">Metody</span><span class="sxs-lookup"><span data-stu-id="6dede-103">Methods</span></span>

<span data-ttu-id="6dede-104">A *metoda* je funkce, který je přidružený k typu.</span><span class="sxs-lookup"><span data-stu-id="6dede-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="6dede-105">V objektově orientované programování metody se používají k vystavení a implementovat funkce a chování objekty a typy.</span><span class="sxs-lookup"><span data-stu-id="6dede-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="6dede-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dede-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="6dede-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dede-107">Remarks</span></span>
<span data-ttu-id="6dede-108">V předchozích syntaxe se zobrazí různé formy metoda deklarace a definice.</span><span class="sxs-lookup"><span data-stu-id="6dede-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="6dede-109">V delší metoda subjekty konec řádku následuje rovná se (=) a metoda celý text odsazeno.</span><span class="sxs-lookup"><span data-stu-id="6dede-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="6dede-110">Atributy je použít pro všechny deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="6dede-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="6dede-111">Tyto předcházet syntaxe definici metody a obvykle jsou uvedeny na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="6dede-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="6dede-112">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6dede-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="6dede-113">Může být označen metody `inline`.</span><span class="sxs-lookup"><span data-stu-id="6dede-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="6dede-114">Informace o `inline`, najdete v části [vložené funkce](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6dede-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="6dede-115">Metody bez vložené může být použité rekurzivně v rámci typu; není nutné explicitně povoleno používat `rec` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6dede-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="6dede-116">Instance metody</span><span class="sxs-lookup"><span data-stu-id="6dede-116">Instance Methods</span></span>
<span data-ttu-id="6dede-117">Instance metody jsou deklarovány s `member` – klíčové slovo a *vlastní identifikátor*, za nímž následují tečkou (.) a název metody a parametry.</span><span class="sxs-lookup"><span data-stu-id="6dede-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="6dede-118">Stejně jako v případě pro `let` vazeb *seznam parametrů* může být vzorek.</span><span class="sxs-lookup"><span data-stu-id="6dede-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="6dede-119">Obvykle je uzavřít metoda objevit parametry v závorkách v podobě řazené kolekce členů, což je způsob, jak metody v jazyce F # při jejich vytváření v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dede-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="6dede-120">Ale curryfikované formuláře (parametry, oddělené mezerami) je běžné, že a dalšími vzory jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="6dede-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="6dede-121">Následující příklad ilustruje definice a použití metody neabstraktní instance.</span><span class="sxs-lookup"><span data-stu-id="6dede-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="6dede-122">V rámci metody instance nepoužívejte vlastní identifikátor přístup pole definované za použití umožňují vazby.</span><span class="sxs-lookup"><span data-stu-id="6dede-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="6dede-123">Při přístupu k ostatním členům a vlastnosti, použijte vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="6dede-123">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="6dede-124">Statické metody</span><span class="sxs-lookup"><span data-stu-id="6dede-124">Static Methods</span></span>
<span data-ttu-id="6dede-125">Klíčové slovo `static` slouží k určení, zda metoda může být volána bez instance a není přidružen k instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="6dede-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="6dede-126">Jinak jsou metody instance metody.</span><span class="sxs-lookup"><span data-stu-id="6dede-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="6dede-127">Příklad v další části ukazuje pole deklarovat s `let` – klíčové slovo, vlastnost členy deklarovat s `member` – klíčové slovo a statickou metodu deklarovat s `static` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6dede-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="6dede-128">Následující příklad ilustruje definice a používání statických metod.</span><span class="sxs-lookup"><span data-stu-id="6dede-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="6dede-129">Předpokládejme, že jsou tyto definice metoda v `SomeType` – třída v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="6dede-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="6dede-130">Abstraktní a virtuální metody</span><span class="sxs-lookup"><span data-stu-id="6dede-130">Abstract and Virtual Methods</span></span>
<span data-ttu-id="6dede-131">Klíčové slovo `abstract` označuje, že metoda má slot virtuální odesílání a nemusí mít definici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="6dede-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="6dede-132">A *virtuální odesílání slotu* je záznam v tabulce interně zachována funkcí, která se používá v době běhu k vyhledání virtuální funkce volá typ objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="6dede-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="6dede-133">Tento mechanismus virtuální odesílání je mechanismus, který implementuje *polymorfismus*, důležitou součást objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="6dede-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="6dede-134">Je třída, která má alespoň jednu metodu abstraktní bez definice *abstraktní třída*, což znamená, že nelze vytvořit žádné instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="6dede-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="6dede-135">Další informace o abstraktní třídy najdete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6dede-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="6dede-136">Deklarace abstraktní metodu nezahrnují těla metody.</span><span class="sxs-lookup"><span data-stu-id="6dede-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="6dede-137">Název metody, je místo toho následovaný dvojtečkou (:) a typ podpis metody.</span><span class="sxs-lookup"><span data-stu-id="6dede-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="6dede-138">Typ podpis metody je stejný jako zobrazená technologii IntelliSense, když krátce umístit ukazatel myši nad název metody v editoru Visual Studio Code, s výjimkou bez názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="6dede-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="6dede-139">Typ podpisy zobrazena překladač fsi.exe, také, když pracujete interaktivně.</span><span class="sxs-lookup"><span data-stu-id="6dede-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="6dede-140">Typ podpis metody je tvořen výpis se typy parametrů, za nímž následuje návratový typ se symboly odpovídající oddělovače.</span><span class="sxs-lookup"><span data-stu-id="6dede-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="6dede-141">Curryfikované parametry jsou odděleny `->` a jsou odděleny řazené kolekce členů parametry `*`.</span><span class="sxs-lookup"><span data-stu-id="6dede-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="6dede-142">Návratová hodnota je vždy oddělená od argumenty podle `->` symbol.</span><span class="sxs-lookup"><span data-stu-id="6dede-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="6dede-143">Závorky lze použít k seskupení komplexní parametrů, třeba když typ funkce je parametr, a určit, kdy řazené kolekce členů je zpracováván jako jeden parametr a nikoli jako dva parametry.</span><span class="sxs-lookup"><span data-stu-id="6dede-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="6dede-144">Můžete také udělit abstraktní metody výchozí definice přidáním definice pro třídu a pomocí `default` – klíčové slovo, jak je znázorněno v syntaxi bloku v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6dede-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="6dede-145">Abstraktní metodu, která má definice ve stejné třídě je ekvivalentní virtuální metodu v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dede-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="6dede-146">Tom, jestli existuje definice, `abstract` – klíčové slovo vytvoří nový odesílání slot v tabulce virtuální funkce pro třídu.</span><span class="sxs-lookup"><span data-stu-id="6dede-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="6dede-147">Bez ohledu na to, jestli základní třída implementuje její abstraktní metody odvozené třídy můžete poskytovat implementace metod abstraktní.</span><span class="sxs-lookup"><span data-stu-id="6dede-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="6dede-148">Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má stejný název a podpis v odvozené třídě, s výjimkou použití `override` nebo `default` – klíčové slovo a zadejte text metoda.</span><span class="sxs-lookup"><span data-stu-id="6dede-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="6dede-149">Klíčová slova `override` a `default` přesně mají stejný význam.</span><span class="sxs-lookup"><span data-stu-id="6dede-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="6dede-150">Použít `override` Pokud nová metoda přepsání základní třída implementace; použijte `default` při vytváření implementaci ve třídě stejné jako původní abstraktní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6dede-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="6dede-151">Nepoužívejte `abstract` – klíčové slovo na metodu, která implementuje metodu, která byla definována jako abstraktní základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6dede-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="6dede-152">Následující příklad ilustruje abstraktní metodu `Rotate` má výchozí implementace ekvivalentní virtuální metody rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dede-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="6dede-153">Následující příklad ilustruje odvozené třídy, který přepíše metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6dede-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="6dede-154">V takovém případě přepsání změní chování tak, aby metoda neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="6dede-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="6dede-155">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="6dede-155">Overloaded Methods</span></span>
<span data-ttu-id="6dede-156">Přetížené metody jsou metody, které mají stejné názvy v daného typu, ale které mají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="6dede-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="6dede-157">V jazyce F # jsou volitelné argumenty obvykle používají místo přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="6dede-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="6dede-158">Přetížené metody však nejsou povolené v jazyce, za předpokladu, že argumenty, které jsou v podobě řazené kolekce členů, není curryfikované formuláře.</span><span class="sxs-lookup"><span data-stu-id="6dede-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="6dede-159">Nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="6dede-159">Optional Arguments</span></span>

<span data-ttu-id="6dede-160">Od verze 4.1 F #, může také mít volitelné argumenty s výchozí hodnotou parametru v metodách.</span><span class="sxs-lookup"><span data-stu-id="6dede-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="6dede-161">Toto je proces zefektivnit vzájemná spolupráce pomocí kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6dede-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="6dede-162">Následující příklad ukazuje syntaxi:</span><span class="sxs-lookup"><span data-stu-id="6dede-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="6dede-163">Všimněte si, že hodnota předaná pro `DefaultParameterValue` vstupní typ se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="6dede-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="6dede-164">V ukázce výše je `int`.</span><span class="sxs-lookup"><span data-stu-id="6dede-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="6dede-165">Probíhá pokus o předání-celé číslo hodnoty do `DefaultParameterValue` by způsobilo chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="6dede-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="6dede-166">Příklad: Vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="6dede-166">Example: Properties and Methods</span></span>
<span data-ttu-id="6dede-167">Následující příklad obsahuje typ, který se příklady pole, privátní funkce, vlastnosti a statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="6dede-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="6dede-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="6dede-168">See Also</span></span>
[<span data-ttu-id="6dede-169">Členové</span><span class="sxs-lookup"><span data-stu-id="6dede-169">Members</span></span>](index.md)
