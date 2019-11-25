---
title: Metody
description: Zjistěte, jak F# je metoda přidružená k typu, který slouží k vystavení a implementaci funkcí a chování objektů a typů.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976649"
---
# <a name="methods"></a><span data-ttu-id="4151d-103">Metody</span><span class="sxs-lookup"><span data-stu-id="4151d-103">Methods</span></span>

<span data-ttu-id="4151d-104">*Metoda* je funkce, která je přidružena k typu.</span><span class="sxs-lookup"><span data-stu-id="4151d-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="4151d-105">V objektově orientovaném programování metody slouží k vystavení a implementaci funkcí a chování objektů a typů.</span><span class="sxs-lookup"><span data-stu-id="4151d-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="4151d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4151d-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4151d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4151d-107">Remarks</span></span>

<span data-ttu-id="4151d-108">V předchozí syntaxi vidíte různé formy deklarací a definic metod.</span><span class="sxs-lookup"><span data-stu-id="4151d-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="4151d-109">V delších textech metod zalomení řádku následuje znaménko rovná se (=) a tělo celé metody se odsadí.</span><span class="sxs-lookup"><span data-stu-id="4151d-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="4151d-110">Atributy lze použít pro jakoukoliv deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="4151d-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="4151d-111">Předcházejí syntaxi pro definici metody a jsou obvykle uvedeny na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="4151d-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="4151d-112">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4151d-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="4151d-113">Metody mohou být označeny `inline`.</span><span class="sxs-lookup"><span data-stu-id="4151d-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="4151d-114">Informace o `inline`naleznete v tématu [inline Functions](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4151d-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="4151d-115">Nevložené metody lze v rámci typu rekurzivně použít. nemusíte explicitně používat klíčové slovo `rec`.</span><span class="sxs-lookup"><span data-stu-id="4151d-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="4151d-116">Metody instance</span><span class="sxs-lookup"><span data-stu-id="4151d-116">Instance Methods</span></span>

<span data-ttu-id="4151d-117">Metody instance jsou deklarovány s klíčovým slovem `member` a *držitelem s identifikátorem*, za kterým následuje tečka (.) a název metody a parametry.</span><span class="sxs-lookup"><span data-stu-id="4151d-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="4151d-118">Stejně jako v případě vazeb `let` může být *seznam parametrů* vzorem.</span><span class="sxs-lookup"><span data-stu-id="4151d-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="4151d-119">Obvykle jsou parametry metody uzavřeny v závorkách v podobě řazené kolekce členů, což je způsob, jakým F# se tyto metody zobrazují v případě, že jsou vytvořeny v jiných .NET Frameworkch jazycích.</span><span class="sxs-lookup"><span data-stu-id="4151d-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="4151d-120">Nicméně formulář curryfikované (parametry oddělené mezerami) je také společný a další vzory jsou podporovány také.</span><span class="sxs-lookup"><span data-stu-id="4151d-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="4151d-121">Následující příklad ukazuje definici a použití neabstraktní metody instance.</span><span class="sxs-lookup"><span data-stu-id="4151d-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="4151d-122">V rámci metod instance nepoužívejte vlastní identifikátor pro přístup k polím definovaným pomocí vazeb let.</span><span class="sxs-lookup"><span data-stu-id="4151d-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="4151d-123">Použijte samotný identifikátor při přístupu k ostatním členům a vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="4151d-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="4151d-124">Statické metody</span><span class="sxs-lookup"><span data-stu-id="4151d-124">Static Methods</span></span>

<span data-ttu-id="4151d-125">Klíčové slovo `static` slouží k určení, že metodu lze volat bez instance a není přidružena k instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="4151d-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="4151d-126">V opačném případě metody jsou metody instance.</span><span class="sxs-lookup"><span data-stu-id="4151d-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="4151d-127">Příklad v další části zobrazuje pole deklarovaná s klíčovým slovem `let`, členy vlastnosti deklarované s klíčovým slovem `member` a statickou metodou deklarovanou klíčovým slovem `static`.</span><span class="sxs-lookup"><span data-stu-id="4151d-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="4151d-128">Následující příklad ukazuje definici a použití statických metod.</span><span class="sxs-lookup"><span data-stu-id="4151d-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="4151d-129">Předpokládají, že tyto definice metod jsou v předchozí části v třídě `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="4151d-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="4151d-130">Abstraktní a virtuální metody</span><span class="sxs-lookup"><span data-stu-id="4151d-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="4151d-131">Klíčové slovo `abstract` označuje, že metoda má virtuální slot pro expedici a nemusí mít definici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="4151d-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="4151d-132">*Virtuální slot pro expedici* je položka ve interně udržované tabulce funkcí, která se používá v době běhu k vyhledání volání virtuální funkce v objektově orientovaném typu.</span><span class="sxs-lookup"><span data-stu-id="4151d-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="4151d-133">Mechanizmus pro virtuální expedici je mechanismus, který implementuje *polymorfismus*, což je důležitá funkce pro objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="4151d-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="4151d-134">Třída, která má alespoň jednu abstraktní metodu bez definice, je *abstraktní třída*, což znamená, že nelze vytvořit žádné instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="4151d-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="4151d-135">Další informace o abstraktních třídách naleznete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="4151d-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="4151d-136">Deklarace abstraktní metody neobsahují tělo metody.</span><span class="sxs-lookup"><span data-stu-id="4151d-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="4151d-137">Místo toho je název metody následován dvojtečkou (:) a podpis typu pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4151d-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="4151d-138">Podpis typu metody je stejný jako typ, který je zobrazen technologií IntelliSense při pozastavení ukazatele myši nad názvem metody v editoru Visual Studio Code, s výjimkou názvů parametrů.</span><span class="sxs-lookup"><span data-stu-id="4151d-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="4151d-139">Signatury typů se zobrazí také překladačem FSI. exe, když pracujete interaktivně.</span><span class="sxs-lookup"><span data-stu-id="4151d-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="4151d-140">Podpis typu metody je tvořen výpisem typů parametrů následovaných návratovým typem s příslušnými symboly oddělovače.</span><span class="sxs-lookup"><span data-stu-id="4151d-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="4151d-141">Parametry curryfikované jsou oddělené `->` a parametry řazené kolekce členů jsou oddělené `*`.</span><span class="sxs-lookup"><span data-stu-id="4151d-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="4151d-142">Vrácená hodnota je vždy oddělená od argumentů symbolem `->`.</span><span class="sxs-lookup"><span data-stu-id="4151d-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="4151d-143">Kulaté závorky lze použít k seskupení složitých parametrů, například, když je typ funkce parametr nebo chcete-li určit, kdy se řazená kolekce členů považuje za jeden parametr, nikoli jako dva parametry.</span><span class="sxs-lookup"><span data-stu-id="4151d-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="4151d-144">Můžete také poskytnout abstraktní metody jako výchozí definice přidáním definice ke třídě a použitím klíčového slova `default`, jak je znázorněno v bloku syntaxe v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4151d-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="4151d-145">Abstraktní metoda, která má definici ve stejné třídě, je ekvivalentní virtuální metodě v jiných .NET Framework jazycích.</span><span class="sxs-lookup"><span data-stu-id="4151d-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="4151d-146">Bez ohledu na to, zda definice existuje, klíčové slovo `abstract` vytvoří novou patici pro expedici v tabulce virtuálních funkcí pro danou třídu.</span><span class="sxs-lookup"><span data-stu-id="4151d-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="4151d-147">Bez ohledu na to, zda základní třída implementuje své abstraktní metody, mohou odvozené třídy poskytnout implementace abstraktních metod.</span><span class="sxs-lookup"><span data-stu-id="4151d-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="4151d-148">Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má stejný název a signaturu v odvozené třídě, s výjimkou použití klíčového slova `override` nebo `default` a zadejte tělo metody.</span><span class="sxs-lookup"><span data-stu-id="4151d-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="4151d-149">Klíčová slova `override` a `default` znamenají naprosto stejnou věc.</span><span class="sxs-lookup"><span data-stu-id="4151d-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="4151d-150">Použijte `override`, pokud nová metoda přepisuje implementaci základní třídy; Použijte `default` při vytváření implementace ve stejné třídě jako původní abstraktní deklarace.</span><span class="sxs-lookup"><span data-stu-id="4151d-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="4151d-151">Nepoužívejte klíčové slovo `abstract` pro metodu, která implementuje metodu, která byla deklarována jako abstraktní v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="4151d-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="4151d-152">Následující příklad ukazuje abstraktní metodu `Rotate`, která má výchozí implementaci, ekvivalent .NET Framework virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="4151d-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="4151d-153">Následující příklad znázorňuje odvozenou třídu, která přepisuje metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4151d-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="4151d-154">V tomto případě přepsání změní chování tak, aby metoda nedělá nic.</span><span class="sxs-lookup"><span data-stu-id="4151d-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="4151d-155">Přetížené metody</span><span class="sxs-lookup"><span data-stu-id="4151d-155">Overloaded Methods</span></span>

<span data-ttu-id="4151d-156">Přetížené metody jsou metody, které mají stejné názvy v daném typu, ale mají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="4151d-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="4151d-157">V F#se obvykle používají volitelné argumenty namísto přetížených metod.</span><span class="sxs-lookup"><span data-stu-id="4151d-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="4151d-158">V jazyce jsou však povoleny přetížené metody za předpokladu, že argumenty jsou v podobě řazené kolekce členů, nikoli curryfikované Form.</span><span class="sxs-lookup"><span data-stu-id="4151d-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="4151d-159">Nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="4151d-159">Optional Arguments</span></span>

<span data-ttu-id="4151d-160">Počínaje F# 4,1 můžete mít v metodách také volitelné argumenty s výchozí hodnotou parametru.</span><span class="sxs-lookup"><span data-stu-id="4151d-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="4151d-161">To usnadňuje práci s C# kódem.</span><span class="sxs-lookup"><span data-stu-id="4151d-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="4151d-162">Následující příklad ukazuje syntaxi:</span><span class="sxs-lookup"><span data-stu-id="4151d-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="4151d-163">Všimněte si, že hodnota předaná pro `DefaultParameterValue` musí odpovídat vstupnímu typu.</span><span class="sxs-lookup"><span data-stu-id="4151d-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="4151d-164">Ve výše uvedeném příkladu se jedná o `int`.</span><span class="sxs-lookup"><span data-stu-id="4151d-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="4151d-165">Při pokusu o předání hodnoty, která není celočíselná, do `DefaultParameterValue` dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="4151d-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="4151d-166">Příklad: vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="4151d-166">Example: Properties and Methods</span></span>

<span data-ttu-id="4151d-167">Následující příklad obsahuje typ obsahující příklady polí, privátních funkcí, vlastností a statické metody.</span><span class="sxs-lookup"><span data-stu-id="4151d-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="4151d-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4151d-168">See also</span></span>

- [<span data-ttu-id="4151d-169">Členové</span><span class="sxs-lookup"><span data-stu-id="4151d-169">Members</span></span>](index.md)
