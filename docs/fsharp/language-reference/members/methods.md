---
title: Metody
description: Zjistěte, jak F# metoda je funkce spojená s typem, které se používají k vystavení a implementaci funkce a chování objektů a typů.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400209"
---
# <a name="methods"></a><span data-ttu-id="9db52-103">Metody</span><span class="sxs-lookup"><span data-stu-id="9db52-103">Methods</span></span>

<span data-ttu-id="9db52-104">*Metoda* je funkce, která je přidružena k typu.</span><span class="sxs-lookup"><span data-stu-id="9db52-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="9db52-105">V objektově orientovaném programování se metody používají k vystavení a implementaci funkcí a chování objektů a typů.</span><span class="sxs-lookup"><span data-stu-id="9db52-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="9db52-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9db52-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9db52-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9db52-107">Remarks</span></span>

<span data-ttu-id="9db52-108">V předchozí syntaxi můžete zobrazit různé formy deklarací metod a definic.</span><span class="sxs-lookup"><span data-stu-id="9db52-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="9db52-109">V delších tělech metod následuje zalomení řádku za rovnítkem (=) a celé tělo metody je odsazeno.</span><span class="sxs-lookup"><span data-stu-id="9db52-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="9db52-110">Atributy lze použít pro libovolnou deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="9db52-111">Předcházejí syntaxi definice metody a jsou obvykle uvedeny na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="9db52-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="9db52-112">Další informace naleznete v [tématu Atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9db52-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="9db52-113">Metody mohou `inline`být označeny .</span><span class="sxs-lookup"><span data-stu-id="9db52-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="9db52-114">Informace o `inline`aplikaci naleznete [v tématu Inline Functions](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9db52-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="9db52-115">Non-inline metody lze použít rekurzivně v rámci typu; není nutné explicitně používat `rec` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9db52-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="9db52-116">Metody instance</span><span class="sxs-lookup"><span data-stu-id="9db52-116">Instance Methods</span></span>

<span data-ttu-id="9db52-117">Metody instance jsou `member` deklarovány pomocí klíčového slova a *vlastního identifikátoru*, následované tečkou (.) a názvem a parametry metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="9db52-118">Stejně jako `let` v případě vazby, *seznam parametrů* může být vzor.</span><span class="sxs-lookup"><span data-stu-id="9db52-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="9db52-119">Parametry metody obvykle uzavřete do závorek ve formě n-tice, což je způsob, jakým se metody zobrazují v jazyce F#, když jsou vytvořeny v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9db52-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="9db52-120">Curried formulář (parametry oddělené mezerami) je však také běžné a další vzory jsou podporovány také.</span><span class="sxs-lookup"><span data-stu-id="9db52-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="9db52-121">Následující příklad ilustruje definici a použití metody neabstraktní instance.</span><span class="sxs-lookup"><span data-stu-id="9db52-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="9db52-122">V rámci metod instance nepoužívejte vlastní identifikátor pro přístup k polím definovaným pomocí vazby let.</span><span class="sxs-lookup"><span data-stu-id="9db52-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="9db52-123">Při přístupu k ostatním členům a vlastnostem použijte vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="9db52-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="9db52-124">Statické metody</span><span class="sxs-lookup"><span data-stu-id="9db52-124">Static Methods</span></span>

<span data-ttu-id="9db52-125">Klíčové `static` slovo se používá k určení, že metodu lze volat bez instance a není přidružena k instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="9db52-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="9db52-126">V opačném případě jsou metody instance.</span><span class="sxs-lookup"><span data-stu-id="9db52-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="9db52-127">Příklad v další části zobrazuje pole `let` deklarovaná s `member` klíčovým slovem, členy `static` vlastností deklarované pomocí klíčového slova a statickou metodu deklarovanou pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="9db52-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="9db52-128">Následující příklad ilustruje definici a použití statických metod.</span><span class="sxs-lookup"><span data-stu-id="9db52-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="9db52-129">Předpokládejme, že tyto definice `SomeType` metod jsou ve třídě v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="9db52-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="9db52-130">Abstraktní a virtuální metody</span><span class="sxs-lookup"><span data-stu-id="9db52-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="9db52-131">Klíčové `abstract` slovo označuje, že metoda má virtuální odeslání slot u nemusí mít definici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="9db52-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="9db52-132">*Virtuální dispečerský slot* je položka v interně udržované tabulce funkcí, která se používá za běhu k vyhlídání volání virtuálních funkcí v objektově orientovaném typu.</span><span class="sxs-lookup"><span data-stu-id="9db52-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="9db52-133">Virtuální expediční mechanismus je mechanismus, který implementuje *polymorfismus*, důležitý rys objektově orientovaného programování.</span><span class="sxs-lookup"><span data-stu-id="9db52-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="9db52-134">Třída, která má alespoň jednu abstraktní metodu bez definice, je *abstraktní třída*, což znamená, že z této třídy nelze vytvořit žádné instance.</span><span class="sxs-lookup"><span data-stu-id="9db52-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="9db52-135">Další informace o abstraktních třídách naleznete v [tématu Abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9db52-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="9db52-136">Deklarace abstraktní metody neobsahují tělo metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="9db52-137">Místo toho název metody následuje dvojtečka (:) a podpis typu pro metodu.</span><span class="sxs-lookup"><span data-stu-id="9db52-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="9db52-138">Typ podpisu metody je stejný jako uvidíte IntelliSense při pozastavení ukazatele myši nad název metody v Editoru kódu Visual Studio, s výjimkou bez názvů parametrů.</span><span class="sxs-lookup"><span data-stu-id="9db52-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="9db52-139">Typ podpisy jsou také zobrazeny interpret, fsi.exe, když pracujete interaktivně.</span><span class="sxs-lookup"><span data-stu-id="9db52-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="9db52-140">Podpis typu metody je tvořen výpisem typů parametrů následovaných návratovým typem s příslušnými oddělovacími symboly.</span><span class="sxs-lookup"><span data-stu-id="9db52-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="9db52-141">Curried parametry jsou `->` odděleny a řazené kolekce členů parametry jsou odděleny `*`.</span><span class="sxs-lookup"><span data-stu-id="9db52-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="9db52-142">Vrácená hodnota je vždy oddělena `->` od argumentů symbolem.</span><span class="sxs-lookup"><span data-stu-id="9db52-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="9db52-143">Závorky lze použít k seskupení složitých parametrů, například když je parametrem typ funkce, nebo k označení, kdy je řazená kolekce členů považována za jeden parametr, nikoli za dva parametry.</span><span class="sxs-lookup"><span data-stu-id="9db52-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="9db52-144">Abstraktní metody můžete také poskytnout výchozí definice přidáním definice `default` do třídy a použitím klíčového slova, jak je znázorněno v bloku syntaxe v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9db52-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="9db52-145">Abstraktní metoda, která má definici ve stejné třídě, je ekvivalentní virtuální metodě v jiných jazycích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9db52-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="9db52-146">Bez ohledu na to, `abstract` zda definice existuje, klíčové slovo vytvoří nový slot odeslání v tabulce virtuálních funkcí pro třídu.</span><span class="sxs-lookup"><span data-stu-id="9db52-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="9db52-147">Bez ohledu na to, zda základní třída implementuje své abstraktní metody, odvozené třídy mohou poskytovat implementace abstraktních metod.</span><span class="sxs-lookup"><span data-stu-id="9db52-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="9db52-148">Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má `override` `default` stejný název a podpis v odvozené třídě, s výjimkou použití klíčového slova nebo a zadejte tělo metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="9db52-149">Klíčová `override` slova `default` a znamenají přesně totéž.</span><span class="sxs-lookup"><span data-stu-id="9db52-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="9db52-150">Použijte, `override` pokud nová metoda přepíše implementaci základní třídy; použijte `default` při vytváření implementace ve stejné třídě jako původní abstraktní deklarace.</span><span class="sxs-lookup"><span data-stu-id="9db52-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="9db52-151">Nepoužívejte `abstract` klíčové slovo na metodu, která implementuje metodu, která byla deklarována abstraktní v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="9db52-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="9db52-152">Následující příklad ilustruje abstraktní `Rotate` metodu, která má výchozí implementaci, ekvivalent virtuální metody rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9db52-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="9db52-153">Následující příklad ilustruje odvozenou třídu, která přepíše metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9db52-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="9db52-154">V tomto případě přepsání změní chování tak, aby metoda neprovede žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="9db52-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="9db52-155">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="9db52-155">Overloaded Methods</span></span>

<span data-ttu-id="9db52-156">Přetížené metody jsou metody, které mají identické názvy v daném typu, ale které mají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="9db52-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="9db52-157">V F# volitelné argumenty se obvykle používají namísto přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="9db52-158">Přetížené metody jsou však povoleny v jazyce, za předpokladu, že argumenty jsou ve formě n-tice, nikoli curried formě.</span><span class="sxs-lookup"><span data-stu-id="9db52-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="9db52-159">Volitelné argumenty</span><span class="sxs-lookup"><span data-stu-id="9db52-159">Optional Arguments</span></span>

<span data-ttu-id="9db52-160">Počínaje F# 4.1, můžete také mít volitelné argumenty s výchozí hodnotou parametru v metodách.</span><span class="sxs-lookup"><span data-stu-id="9db52-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="9db52-161">To pomáhá usnadnit spolupráci s kódem Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9db52-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="9db52-162">Následující příklad ukazuje syntaxi:</span><span class="sxs-lookup"><span data-stu-id="9db52-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="9db52-163">Všimněte si, že `DefaultParameterValue` hodnota předaná pro musí odpovídat vstupnímu typu.</span><span class="sxs-lookup"><span data-stu-id="9db52-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="9db52-164">Ve výše uvedeném vzorku `int`se jedná o .</span><span class="sxs-lookup"><span data-stu-id="9db52-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="9db52-165">Pokus o předání hodnoty necelého `DefaultParameterValue` čísla by mělo za následek chybu kompilace.</span><span class="sxs-lookup"><span data-stu-id="9db52-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="9db52-166">Příklad: Vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="9db52-166">Example: Properties and Methods</span></span>

<span data-ttu-id="9db52-167">Následující příklad obsahuje typ, který obsahuje příklady polí, soukromých funkcí, vlastností a statické metody.</span><span class="sxs-lookup"><span data-stu-id="9db52-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="9db52-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="9db52-168">See also</span></span>

- [<span data-ttu-id="9db52-169">Členové</span><span class="sxs-lookup"><span data-stu-id="9db52-169">Members</span></span>](index.md)
