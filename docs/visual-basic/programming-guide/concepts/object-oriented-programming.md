---
title: Objektově orientované programování (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297085"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="349d1-102">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="349d1-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="349d1-103">Visual Basic poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.</span><span class="sxs-lookup"><span data-stu-id="349d1-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="349d1-104">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="349d1-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="349d1-105">*Dědičnost* popisuje schopnost vytvářet nové třídy na základě existující třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="349d1-106">*Polymorfismus* znamená, že můžete mít více tříd, které můžete používat Zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="349d1-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="349d1-107">Tato část popisuje následující pojmy:</span><span class="sxs-lookup"><span data-stu-id="349d1-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="349d1-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="349d1-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="349d1-109">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="349d1-110">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="349d1-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="349d1-111">Metody</span><span class="sxs-lookup"><span data-stu-id="349d1-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="349d1-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="349d1-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="349d1-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="349d1-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="349d1-114">Události</span><span class="sxs-lookup"><span data-stu-id="349d1-114">Events</span></span>](#events)
    - [<span data-ttu-id="349d1-115">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="349d1-116">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="349d1-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="349d1-117">Vytvoření instance třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="349d1-118">Sdílené třídy a členy</span><span class="sxs-lookup"><span data-stu-id="349d1-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="349d1-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="349d1-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="349d1-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="349d1-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="349d1-121">Obejití členů</span><span class="sxs-lookup"><span data-stu-id="349d1-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="349d1-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="349d1-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="349d1-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="349d1-123">Generics</span></span>](#generics)
- [<span data-ttu-id="349d1-124">Delegáti</span><span class="sxs-lookup"><span data-stu-id="349d1-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="349d1-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="349d1-125">Classes and objects</span></span>

<span data-ttu-id="349d1-126">Podmínky *třídy* a *objekt* se někdy používají vzájemné záměně, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd.</span><span class="sxs-lookup"><span data-stu-id="349d1-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="349d1-127">Ano, je volána při vytvoření objektu *instance*.</span><span class="sxs-lookup"><span data-stu-id="349d1-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="349d1-128">Při použití analogie matric, třída je podrobný plán a objekt je vytvořen z této matrice budovy.</span><span class="sxs-lookup"><span data-stu-id="349d1-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="349d1-129">Definování třídy:</span><span class="sxs-lookup"><span data-stu-id="349d1-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="349d1-130">Visual Basic také nabízí jednodušší verzi tříd pojmenovanou *struktury* , které jsou užitečné, když budete chtít vytvořit velké pole objektů a proveďte k tomu k tomu spotřebovat příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="349d1-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="349d1-131">Definování struktury:</span><span class="sxs-lookup"><span data-stu-id="349d1-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="349d1-132">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-132">For more information, see:</span></span>

- [<span data-ttu-id="349d1-133">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="349d1-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="349d1-134">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="349d1-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="349d1-135">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-135">Class members</span></span>

<span data-ttu-id="349d1-136">Každá třída může mít různé *členy třídy* obsahující vlastnosti, které popisují data třídy, metody, které určují chování třídy a události, které umožňují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="349d1-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="349d1-137">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="349d1-137">Properties and fields</span></span>

<span data-ttu-id="349d1-138">Pole a vlastnosti představují informace, které obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="349d1-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="349d1-139">Pole jsou jako proměnné, protože mohou být čtena nebo nastavena přímo.</span><span class="sxs-lookup"><span data-stu-id="349d1-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="349d1-140">Definování pole:</span><span class="sxs-lookup"><span data-stu-id="349d1-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="349d1-141">Vlastnosti mají get a nastavte postupy, které poskytují větší kontrolu toho, jak jsou hodnoty nastavena nebo vrácena.</span><span class="sxs-lookup"><span data-stu-id="349d1-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="349d1-142">Visual Basic můžete buď vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí a poskytnou základní logiku pro procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="349d1-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="349d1-143">Chcete-li definovat automaticky implementovanou vlastnost:</span><span class="sxs-lookup"><span data-stu-id="349d1-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="349d1-144">Pokud je potřeba provést některé další operace čtení a zápisu hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro ukládání a načítání:</span><span class="sxs-lookup"><span data-stu-id="349d1-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="349d1-145">Většina vlastností má metody nebo postupy, jak nastavit a získat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="349d1-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="349d1-146">Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, abyste omezili je číst nebo upravovat.</span><span class="sxs-lookup"><span data-stu-id="349d1-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="349d1-147">V jazyce Visual Basic můžete použít `ReadOnly` a `WriteOnly` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="349d1-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="349d1-148">Automaticky implementované vlastnosti nemůže být ale jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="349d1-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="349d1-149">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-149">For more information, see:</span></span>

- [<span data-ttu-id="349d1-150">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="349d1-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="349d1-151">Příkaz Get</span><span class="sxs-lookup"><span data-stu-id="349d1-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="349d1-152">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="349d1-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="349d1-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="349d1-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="349d1-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="349d1-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="349d1-155">Metody</span><span class="sxs-lookup"><span data-stu-id="349d1-155">Methods</span></span>

 <span data-ttu-id="349d1-156">A *metoda* je akce, které může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="349d1-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="349d1-157">V jazyce Visual Basic existují dva způsoby, jak vytvořit metodu: `Sub` prohlášení se používá, pokud metoda nevrací hodnotu `Function` prohlášení se používá, pokud metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="349d1-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="349d1-158">Chcete-li definovat metodu pro třídu:</span><span class="sxs-lookup"><span data-stu-id="349d1-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="349d1-159">Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se liší v počtu parametrů nebo typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="349d1-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="349d1-160">Chcete-li přetížit metodu:</span><span class="sxs-lookup"><span data-stu-id="349d1-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="349d1-161">Ve většině případů deklarujete metodu v rámci definice třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="349d1-162">Ale také podporuje jazyka Visual Basic *rozšiřující metody* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="349d1-163">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-163">For more information, see:</span></span>

- [<span data-ttu-id="349d1-164">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="349d1-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="349d1-165">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="349d1-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="349d1-166">Overloads</span><span class="sxs-lookup"><span data-stu-id="349d1-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="349d1-167">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="349d1-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="349d1-168">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="349d1-168">Constructors</span></span>

<span data-ttu-id="349d1-169">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="349d1-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="349d1-170">Konstruktory obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="349d1-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="349d1-171">Konstruktor lze spustit pouze jednou při vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="349d1-172">Kromě toho kód v konstruktoru se vždy spouští před ostatním kódem ve třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="349d1-173">Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoliv jiné metody.</span><span class="sxs-lookup"><span data-stu-id="349d1-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="349d1-174">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="349d1-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="349d1-175">Další informace najdete v tématu: [doba života objektu: jak objekty jsou vytvořená a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="349d1-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="349d1-176">Destructors</span></span>

<span data-ttu-id="349d1-177">Destruktory se používají k destrukci instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="349d1-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="349d1-178">V rozhraní .NET Framework systému uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="349d1-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="349d1-179">Můžete však stále potřebovat destruktory pro vyčištění všech nespravovaných prostředků, které vytváří vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="349d1-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="349d1-180">Může existovat pouze jeden destruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="349d1-181">Další informace o destruktorech a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="349d1-182">Události</span><span class="sxs-lookup"><span data-stu-id="349d1-182">Events</span></span>

<span data-ttu-id="349d1-183">Události umožňují třídám nebo objektům upozornit ostatní třídy nebo objekty, když něco, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="349d1-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="349d1-184">Třída, která odesílá (nebo vyvolává) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *předplatitele*.</span><span class="sxs-lookup"><span data-stu-id="349d1-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="349d1-185">Další informace o událostech, jak jejich vyvolávání a zpracování viz [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="349d1-186">Chcete-li deklarovat události, použijte [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="349d1-187">Chcete-li vyvolat události, použijte [RaiseEvent – příkaz](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="349d1-188">Chcete-li určit obslužné rutiny událostí deklarativním způsobem, použijte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) příkazu a [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="349d1-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="349d1-189">Aby bylo možné dynamicky přidat, odebrat a změnit obslužnou rutinu události, který je přidružený k události, použijte [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md) a [RemoveHandler – příkaz](../../../visual-basic/language-reference/statements/removehandler-statement.md) spolu s [AddressOf Operátor](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="349d1-190">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-190">Nested classes</span></span>

<span data-ttu-id="349d1-191">Třída definována v rámci jiné třídy se nazývá *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="349d1-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="349d1-192">Ve výchozím nastavení vnořené třídy je privátní.</span><span class="sxs-lookup"><span data-stu-id="349d1-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="349d1-193">Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaného tečkou a pak následovaného názvem vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="349d1-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="349d1-194">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="349d1-194">Access modifiers and access levels</span></span>

<span data-ttu-id="349d1-195">Všechny třídy a členy třídy můžete určit úroveň přístupu poskytují dalším třídám, pomocí *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="349d1-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="349d1-196">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="349d1-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="349d1-197">Visual Basic modifikátor</span><span class="sxs-lookup"><span data-stu-id="349d1-197">Visual Basic Modifier</span></span>|<span data-ttu-id="349d1-198">Definice</span><span class="sxs-lookup"><span data-stu-id="349d1-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="349d1-199">Public</span><span class="sxs-lookup"><span data-stu-id="349d1-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="349d1-200">Tento typ nebo člen je přístupný libovolnému jinému kódu ve stejném sestavení nebo libovolnému sestavení která na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="349d1-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="349d1-201">Private</span><span class="sxs-lookup"><span data-stu-id="349d1-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="349d1-202">Tento typ nebo člen je přístupný pouze kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="349d1-203">Protected</span><span class="sxs-lookup"><span data-stu-id="349d1-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="349d1-204">Tento typ nebo člen je přístupný pouze kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="349d1-205">Friend</span><span class="sxs-lookup"><span data-stu-id="349d1-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="349d1-206">Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, ale ne z jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="349d1-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="349d1-207">Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, nebo kterékoli odvozené třídě v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="349d1-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="349d1-208">Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="349d1-209">Vytvoření instance třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-209">Instantiating classes</span></span>

<span data-ttu-id="349d1-210">Pro vytvoření objektu, budete muset vytvořit instanci třídy, nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="349d1-211">Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a volat metody třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="349d1-212">Chcete-li přiřadit hodnoty vlastností během procesu vytváření instance třídy, použijte inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="349d1-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="349d1-213">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-213">For more information, see:</span></span>

- [<span data-ttu-id="349d1-214">Operátor New</span><span class="sxs-lookup"><span data-stu-id="349d1-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="349d1-215">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="349d1-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="349d1-216">Sdílené třídy a členy</span><span class="sxs-lookup"><span data-stu-id="349d1-216">Shared classes and members</span></span>

 <span data-ttu-id="349d1-217">Sdílenému členu třídy je vlastnost, procedura nebo pole, která je sdílena všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="349d1-218">Chcete-li definovat sdílenému členu:</span><span class="sxs-lookup"><span data-stu-id="349d1-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="349d1-219">Chcete-li přístup ke sdílenému členu, použijte název třídy bez vytvoření objektů této třídy:</span><span class="sxs-lookup"><span data-stu-id="349d1-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="349d1-220">Sdílené moduly v jazyce Visual Basic sdíleli pouze členy a nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="349d1-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="349d1-221">Sdílené členy také nelze přistupovat k vlastnosti nesdílené, polím nebo metodám</span><span class="sxs-lookup"><span data-stu-id="349d1-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="349d1-222">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-222">For more information, see:</span></span>

- [<span data-ttu-id="349d1-223">Shared</span><span class="sxs-lookup"><span data-stu-id="349d1-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="349d1-224">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="349d1-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="349d1-225">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="349d1-225">Anonymous types</span></span>

<span data-ttu-id="349d1-226">Anonymní typy umožňují vytvářet objekty bez psaní definice třídy datového typu.</span><span class="sxs-lookup"><span data-stu-id="349d1-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="349d1-227">Místo toho kompilátor vygeneruje třídu za vás.</span><span class="sxs-lookup"><span data-stu-id="349d1-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="349d1-228">Třída nemá žádný použitelný název a obsahuje vlastnosti, které jste zadali v rámci deklarace objektu.</span><span class="sxs-lookup"><span data-stu-id="349d1-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="349d1-229">Chcete-li vytvořit instanci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="349d1-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="349d1-230">Další informace najdete v tématu: [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="349d1-231">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="349d1-231">Inheritance</span></span>

<span data-ttu-id="349d1-232">Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="349d1-233">Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*, a názvem třídy, která dědí tyto členy *odvozené třídy*.</span><span class="sxs-lookup"><span data-stu-id="349d1-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="349d1-234">Nicméně všechny třídy v jazyce Visual Basic implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně všem třídám.</span><span class="sxs-lookup"><span data-stu-id="349d1-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="349d1-235">Visual Basic nepodporuje vícenásobnou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="349d1-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="349d1-236">To znamená můžete zadat pouze jednu základní třídu pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="349d1-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="349d1-237">Chcete-li dědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="349d1-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="349d1-238">Ve výchozím nastavení je možné zdědit všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-238">By default all classes can be inherited.</span></span> <span data-ttu-id="349d1-239">Můžete však určit, zda třída nesmí používat jako základní třída nebo vytvořit třídu, která lze použít jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="349d1-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="349d1-240">Chcete-li určit, že třídu nelze použít jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="349d1-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="349d1-241">Určíte, že třída může sloužit jako základní třídu a nelze vytvořit instanci:</span><span class="sxs-lookup"><span data-stu-id="349d1-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="349d1-242">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-242">For more information, see:</span></span>

- [<span data-ttu-id="349d1-243">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="349d1-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="349d1-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="349d1-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="349d1-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="349d1-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="349d1-246">Obejití členů</span><span class="sxs-lookup"><span data-stu-id="349d1-246">Overriding members</span></span>

<span data-ttu-id="349d1-247">Ve výchozím nastavení dědí odvozená třída všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="349d1-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="349d1-248">Pokud chcete změnit chování zděděného člena, musíte ho potlačit.</span><span class="sxs-lookup"><span data-stu-id="349d1-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="349d1-249">To znamená můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="349d1-250">Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="349d1-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="349d1-251">Visual Basic modifikátor</span><span class="sxs-lookup"><span data-stu-id="349d1-251">Visual Basic Modifier</span></span>|<span data-ttu-id="349d1-252">Definice</span><span class="sxs-lookup"><span data-stu-id="349d1-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="349d1-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="349d1-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="349d1-254">Umožňuje člen třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="349d1-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="349d1-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="349d1-256">Přepsání virtuální (s možností přepsání) člena definovaného v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="349d1-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="349d1-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="349d1-258">Zabrání přepsání v dědičné třídě člena.</span><span class="sxs-lookup"><span data-stu-id="349d1-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="349d1-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="349d1-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="349d1-260">Vyžaduje, aby člen třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="349d1-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="349d1-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="349d1-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="349d1-262">Skryje člena zděděného ze základní třídy</span><span class="sxs-lookup"><span data-stu-id="349d1-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="349d1-263">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="349d1-263">Interfaces</span></span>

<span data-ttu-id="349d1-264">Rozhraní, stejně jako třídy, definují sadu vlastností, metody a události.</span><span class="sxs-lookup"><span data-stu-id="349d1-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="349d1-265">Ale na rozdíl od tříd, rozhraní neposkytují implementace.</span><span class="sxs-lookup"><span data-stu-id="349d1-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="349d1-266">Jsou implementované třídami a definovány jako samostatné subjekty ze tříd.</span><span class="sxs-lookup"><span data-stu-id="349d1-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="349d1-267">Rozhraní představuje smlouvu v tom, že třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.</span><span class="sxs-lookup"><span data-stu-id="349d1-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="349d1-268">Definování rozhraní:</span><span class="sxs-lookup"><span data-stu-id="349d1-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="349d1-269">Pro implementaci rozhraní ve třídě:</span><span class="sxs-lookup"><span data-stu-id="349d1-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="349d1-270">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-270">For more information, see:</span></span>

- [<span data-ttu-id="349d1-271">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="349d1-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="349d1-272">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="349d1-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="349d1-273">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="349d1-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="349d1-274">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="349d1-274">Generics</span></span>

<span data-ttu-id="349d1-275">Třídy, struktury, rozhraní a metody v rozhraní .NET může zahrnovat *parametry typu* , které definují typy objektů, které lze uložit nebo použít.</span><span class="sxs-lookup"><span data-stu-id="349d1-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="349d1-276">Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektu, který bude uložen do kolekce.</span><span class="sxs-lookup"><span data-stu-id="349d1-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="349d1-277">Chcete-li definovat obecnou třídu:</span><span class="sxs-lookup"><span data-stu-id="349d1-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="349d1-278">Vytvoření instance generické třídy:</span><span class="sxs-lookup"><span data-stu-id="349d1-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="349d1-279">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-279">For more information, see:</span></span>

- [<span data-ttu-id="349d1-280">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="349d1-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="349d1-281">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="349d1-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="349d1-282">Delegáty</span><span class="sxs-lookup"><span data-stu-id="349d1-282">Delegates</span></span>

 <span data-ttu-id="349d1-283">A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na jakoukoli metodu s kompatibilním podpisem.</span><span class="sxs-lookup"><span data-stu-id="349d1-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="349d1-284">Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="349d1-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="349d1-285">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="349d1-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="349d1-286">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="349d1-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="349d1-287">Další informace o použití delegátů při zpracování událostí naleznete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="349d1-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="349d1-288">K vytvoření delegáta:</span><span class="sxs-lookup"><span data-stu-id="349d1-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="349d1-289">Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu zadanému delegátem:</span><span class="sxs-lookup"><span data-stu-id="349d1-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="349d1-290">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="349d1-290">For more information, see:</span></span>

- [<span data-ttu-id="349d1-291">Delegáti</span><span class="sxs-lookup"><span data-stu-id="349d1-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="349d1-292">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="349d1-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="349d1-293">Operátor AddressOf</span><span class="sxs-lookup"><span data-stu-id="349d1-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="349d1-294">Viz také:</span><span class="sxs-lookup"><span data-stu-id="349d1-294">See also</span></span>

- [<span data-ttu-id="349d1-295">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="349d1-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
