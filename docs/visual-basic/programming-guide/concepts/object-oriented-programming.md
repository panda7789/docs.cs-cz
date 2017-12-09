---
title: "Objektově orientované programování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 950f080949dce0fc1a2834825d2f7c945007fb7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="de6ee-102">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de6ee-102">Object-Oriented Programming (Visual Basic)</span></span>
<span data-ttu-id="de6ee-103">Visual Basic poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnost a polymorfismus.</span><span class="sxs-lookup"><span data-stu-id="de6ee-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="de6ee-104">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="de6ee-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="de6ee-105">*Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="de6ee-106">*Polymorfismus* znamená, že můžete mít více tříd, které lze použít zcela zaměnitelným významem, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="de6ee-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="de6ee-107">Tato část popisuje následující koncepty:</span><span class="sxs-lookup"><span data-stu-id="de6ee-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="de6ee-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="de6ee-108">Classes and objects</span></span>](#classes-and-objects)  
  
    -   [<span data-ttu-id="de6ee-109">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-109">Class members</span></span>](#members)  
  
         [<span data-ttu-id="de6ee-110">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="de6ee-110">Properties and fields</span></span>](#properties-and-fields)  
  
         [<span data-ttu-id="de6ee-111">Metody</span><span class="sxs-lookup"><span data-stu-id="de6ee-111">Methods</span></span>](#methods)  
  
         [<span data-ttu-id="de6ee-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="de6ee-112">Constructors</span></span>](#constructors)  
  
         [<span data-ttu-id="de6ee-113">Destruktory</span><span class="sxs-lookup"><span data-stu-id="de6ee-113">Destructors</span></span>](#destructors)  
  
         [<span data-ttu-id="de6ee-114">Události</span><span class="sxs-lookup"><span data-stu-id="de6ee-114">Events</span></span>](#events)  
  
         [<span data-ttu-id="de6ee-115">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-115">Nested classes</span></span>](#nested-classes)  
  
    -   [<span data-ttu-id="de6ee-116">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="de6ee-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)  
  
    -   [<span data-ttu-id="de6ee-117">Vytváření instancí třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-117">Instantiating classes</span></span>](#instantiating-classes)  
  
    -   [<span data-ttu-id="de6ee-118">Sdílené třídy a členové</span><span class="sxs-lookup"><span data-stu-id="de6ee-118">Shared classes and members</span></span>](#shared-classes-and-members)  
  
    -   [<span data-ttu-id="de6ee-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-119">Anonymous types</span></span>](#anonymous-types)  
  
-   [<span data-ttu-id="de6ee-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="de6ee-120">Inheritance</span></span>](#inheritance)  
  
    -   [<span data-ttu-id="de6ee-121">Přepis členů</span><span class="sxs-lookup"><span data-stu-id="de6ee-121">Overriding members</span></span>](#overriding-members)  
  
-   [<span data-ttu-id="de6ee-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6ee-122">Interfaces</span></span>](#interfaces)  
  
-   [<span data-ttu-id="de6ee-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-123">Generics</span></span>](#generics)  
  
-   [<span data-ttu-id="de6ee-124">Delegáti</span><span class="sxs-lookup"><span data-stu-id="de6ee-124">Delegates</span></span>](#delegates)  
  
## <a name="classes-and-objects"></a><span data-ttu-id="de6ee-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="de6ee-125">Classes and objects</span></span>  
<span data-ttu-id="de6ee-126">Podmínky *třída* a *objekt* se někdy používají zcela zaměnitelným významem, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd.</span><span class="sxs-lookup"><span data-stu-id="de6ee-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="de6ee-127">Ano, je volána v rámci vytvoření objektu *vytváření instancí*.</span><span class="sxs-lookup"><span data-stu-id="de6ee-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="de6ee-128">Pomocí analogie plán, podle kterého, třída je plán, podle kterého a v budově z tento plán, podle kterého je objekt.</span><span class="sxs-lookup"><span data-stu-id="de6ee-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="de6ee-129">Chcete-li definovat třídu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-129">To define a class:</span></span>

```vb  
Class SampleClass
End Class
```

<span data-ttu-id="de6ee-130">Visual Basic také poskytuje světla verzi třídy názvem *struktury* , jsou užitečné, když potřebujete vytvořit velké pole objektů a proveďte využívat příliš mnoho paměti, pro který chcete.</span><span class="sxs-lookup"><span data-stu-id="de6ee-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="de6ee-131">Chcete-li definovat strukturu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-131">To define a structure:</span></span>  

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="de6ee-132">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-132">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-133">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="de6ee-134">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="de6ee-135">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-135">Class members</span></span>
<span data-ttu-id="de6ee-136">Každá třída může mít různé *třídy členy* , zahrnout vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které zajišťují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="de6ee-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="de6ee-137">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="de6ee-137">Properties and fields</span></span>
<span data-ttu-id="de6ee-138">Pole a vlastnosti představují informací, které obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="de6ee-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="de6ee-139">Pole jsou jako proměnné, protože můžou být číst nebo nastavovat přímo.</span><span class="sxs-lookup"><span data-stu-id="de6ee-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="de6ee-140">Chcete-li definovat pole:</span><span class="sxs-lookup"><span data-stu-id="de6ee-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="de6ee-141">Vlastnosti mají get a nastavte postupů, které poskytuje větší kontrolu na tom, jak nastavit nebo vrátil hodnoty.</span><span class="sxs-lookup"><span data-stu-id="de6ee-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="de6ee-142">Visual Basic můžete buď k vytvoření soukromé pole pro ukládání hodnota vlastnosti nebo takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí, které poskytují základní logiku pro vlastnost postupy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="de6ee-143">Chcete-li definovat ve automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="de6ee-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="de6ee-144">Pokud potřebujete provést některé další operace pro čtení a zápis hodnota vlastnosti definice pole pro ukládání hodnota vlastnosti a poskytují základní logiku pro ukládání a načítání ho:</span><span class="sxs-lookup"><span data-stu-id="de6ee-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

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

<span data-ttu-id="de6ee-145">Většina vlastnosti mají metody nebo postupy, jak nastavit a získat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="de6ee-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="de6ee-146">Můžete však vytvořit vlastnosti jen pro čtení, nebo jen pro zápis je omezit změnit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="de6ee-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="de6ee-147">V jazyce Visual Basic můžete použít `ReadOnly` a `WriteOnly` klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="de6ee-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="de6ee-148">Automaticky implementované vlastnosti však nemůže být jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="de6ee-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="de6ee-149">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-149">For more information, see:</span></span>
  
-   [<span data-ttu-id="de6ee-150">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="de6ee-151">Get – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [<span data-ttu-id="de6ee-152">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [<span data-ttu-id="de6ee-153">Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="de6ee-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [<span data-ttu-id="de6ee-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="de6ee-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a><span data-ttu-id="de6ee-155">Metody</span><span class="sxs-lookup"><span data-stu-id="de6ee-155">Methods</span></span>  
 <span data-ttu-id="de6ee-156">A *metoda* je akce, která může provádět objekt.</span><span class="sxs-lookup"><span data-stu-id="de6ee-156">A *method* is an action that an object can perform.</span></span>  

> [!NOTE]
>  <span data-ttu-id="de6ee-157">V jazyce Visual Basic, existují dva způsoby vytvoření metodu: `Sub` se použije příkaz, pokud metoda nevrátí hodnotu `Function` se použije příkaz, pokud metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="de6ee-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="de6ee-158">Definovat metodu třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="de6ee-159">Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se budou lišit v počtu parametry nebo typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="de6ee-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="de6ee-160">Chcete-li přetížení metody:</span><span class="sxs-lookup"><span data-stu-id="de6ee-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="de6ee-161">Ve většině případů deklarujte metodu v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="de6ee-162">Však také podporuje jazyka Visual Basic *rozšiřující metody* které umožňují přidání metody do existující třídy mimo skutečné definice třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="de6ee-163">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-163">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-164">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  

- [<span data-ttu-id="de6ee-165">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [<span data-ttu-id="de6ee-166">Přetížení</span><span class="sxs-lookup"><span data-stu-id="de6ee-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [<span data-ttu-id="de6ee-167">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="de6ee-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a><span data-ttu-id="de6ee-168">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="de6ee-168">Constructors</span></span>  
<span data-ttu-id="de6ee-169">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="de6ee-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="de6ee-170">Konstruktory obvykle inicializovat datových členů nového objektu.</span><span class="sxs-lookup"><span data-stu-id="de6ee-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="de6ee-171">Konstruktor lze spustit pouze po vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="de6ee-172">Kromě toho kód v konstruktoru vždy spouští před jakýkoli jiný kód v třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="de6ee-173">Můžete však vytvořit více přetížení konstruktor stejným způsobem jako u jakékoliv jiné metody.</span><span class="sxs-lookup"><span data-stu-id="de6ee-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="de6ee-174">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

<span data-ttu-id="de6ee-175">Další informace najdete v tématu: [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="de6ee-176">Destruktory</span><span class="sxs-lookup"><span data-stu-id="de6ee-176">Destructors</span></span>
<span data-ttu-id="de6ee-177">Destruktory se používají k destruct instance tříd.</span><span class="sxs-lookup"><span data-stu-id="de6ee-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="de6ee-178">V rozhraní .NET Framework bude systém uvolňování automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="de6ee-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="de6ee-179">Může však stále zapotřebí destruktory vyčistit všechny nespravovaných prostředků, které vytváří vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="de6ee-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="de6ee-180">Může existovat jenom jeden destruktor pro třídu.</span><span class="sxs-lookup"><span data-stu-id="de6ee-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="de6ee-181">Další informace o destruktory a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="de6ee-182">Události</span><span class="sxs-lookup"><span data-stu-id="de6ee-182">Events</span></span>
<span data-ttu-id="de6ee-183">Události povolit třídu nebo objekt, který chcete upozornit ostatní třídy nebo objekty, když něco zájmu dojde.</span><span class="sxs-lookup"><span data-stu-id="de6ee-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="de6ee-184">Třída, která odešle (nebo vyvolá) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *Odběratelé, kteří*.</span><span class="sxs-lookup"><span data-stu-id="de6ee-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="de6ee-185">Další informace o událostech, způsob jejich jsou vyvolány a zpracovávají, najdete v části [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="de6ee-186">Chcete-li deklarovat události, použijte [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="de6ee-187">Chcete-li vyvolávání událostí, použijte [RaiseEvent – příkaz](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="de6ee-188">Pokud chcete zadat obslužných rutin událostí pomocí deklarativní způsob, použijte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) příkaz a [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="de6ee-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="de6ee-189">Abyste mohli dynamicky přidat, odebrat a změnit obslužné rutiny události přidružený k události, použijte [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md) a [RemoveHandler – příkaz](../../../visual-basic/language-reference/statements/removehandler-statement.md) společně s [AddressOf Operátor](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="de6ee-190">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-190">Nested classes</span></span>  
<span data-ttu-id="de6ee-191">Třídy definované v rámci jiné třídy se nazývá *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="de6ee-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="de6ee-192">Ve výchozím nastavení je vnořené třídy soukromé.</span><span class="sxs-lookup"><span data-stu-id="de6ee-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="de6ee-193">K vytvoření instance třídy vnořené, použijte název třídy kontejneru, za nímž následuje tečky a po ní následuje název vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="de6ee-194">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="de6ee-194">Access modifiers and access levels</span></span>  
<span data-ttu-id="de6ee-195">Všechny třídy a jejich členové můžete určit, jakou úroveň přístupu poskytují další třídy pomocí *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="de6ee-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="de6ee-196">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="de6ee-197">Modifikátor jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de6ee-197">Visual Basic Modifier</span></span>|<span data-ttu-id="de6ee-198">Definice</span><span class="sxs-lookup"><span data-stu-id="de6ee-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="de6ee-199">Veřejné</span><span class="sxs-lookup"><span data-stu-id="de6ee-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="de6ee-200">Typ nebo člen je přístupná jiným kódem ve stejném sestavení nebo jiné sestavení, které na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="de6ee-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="de6ee-201">Privátní</span><span class="sxs-lookup"><span data-stu-id="de6ee-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="de6ee-202">Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="de6ee-203">Chráněný</span><span class="sxs-lookup"><span data-stu-id="de6ee-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="de6ee-204">Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="de6ee-205">Friend</span><span class="sxs-lookup"><span data-stu-id="de6ee-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="de6ee-206">Typ nebo člen je přístupný kód ve stejném sestavení, ale nikoli z jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="de6ee-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="de6ee-207">Typ nebo člen je přístupná žádný kód ve stejném sestavení, nebo všechny odvozené třídy v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="de6ee-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="de6ee-208">Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="de6ee-209">Vytváření instancí třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-209">Instantiating classes</span></span>  
<span data-ttu-id="de6ee-210">Pro vytvoření objektu, musíte vytvořit instanci třídy, nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="de6ee-211">Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a vyvolání metody třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="de6ee-212">Chcete-li přiřadit hodnoty k vlastnosti během procesu vytváření instancí třídy, použijte inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="de6ee-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="de6ee-213">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-213">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-214">New – operátor</span><span class="sxs-lookup"><span data-stu-id="de6ee-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)

- [<span data-ttu-id="de6ee-215">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a><span data-ttu-id="de6ee-216">Sdílené třídy a členové</span><span class="sxs-lookup"><span data-stu-id="de6ee-216">Shared Classes and Members</span></span>  
 <span data-ttu-id="de6ee-217">Sdíleného člena třídy je vlastnost, postup nebo pole, které platí pro všechny instance třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="de6ee-218">Chcete-li definovat sdíleného člena:</span><span class="sxs-lookup"><span data-stu-id="de6ee-218">To define a shared member:</span></span>  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 <span data-ttu-id="de6ee-219">Přístup sdíleného člena, použijte název třídy bez vytvoření objektu této třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 <span data-ttu-id="de6ee-220">Sdílené moduly v jazyce Visual Basic sdíleli pouze členy a nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="de6ee-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="de6ee-221">Sdílení členové také přístup k vlastnosti nesdílené, pole a metody</span><span class="sxs-lookup"><span data-stu-id="de6ee-221">Shared members also cannot access non-shared properties, fields or methods</span></span>  
  
 <span data-ttu-id="de6ee-222">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-222">For more information, see:</span></span>  
  
-   [<span data-ttu-id="de6ee-223">Sdílené</span><span class="sxs-lookup"><span data-stu-id="de6ee-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [<span data-ttu-id="de6ee-224">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a><span data-ttu-id="de6ee-225">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-225">Anonymous types</span></span>  
<span data-ttu-id="de6ee-226">Anonymní typy umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="de6ee-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="de6ee-227">Kompilátor místo, vygeneruje třídu pro vás.</span><span class="sxs-lookup"><span data-stu-id="de6ee-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="de6ee-228">Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklarace objektu.</span><span class="sxs-lookup"><span data-stu-id="de6ee-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="de6ee-229">Chcete-li vytvořit instanci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="de6ee-230">Další informace najdete v tématu: [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="de6ee-231">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="de6ee-231">Inheritance</span></span>
<span data-ttu-id="de6ee-232">Dědičnost umožňuje vytvořit novou třídu, která opětovně používá rozšiřuje a mění chování, která je definována v jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="de6ee-233">Je volána třídu, jejíž členové jsou děděné *základní třída*, a třídu, která dědí členů, se nazývá *odvozené třídy*.</span><span class="sxs-lookup"><span data-stu-id="de6ee-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="de6ee-234">Ale všechny třídy v jazyce Visual Basic implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchie tříd rozhraní .NET a poskytuje nižší úroveň služby pro všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
>  <span data-ttu-id="de6ee-235">Visual Basic nepodporuje vícenásobná dědičnost.</span><span class="sxs-lookup"><span data-stu-id="de6ee-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="de6ee-236">To znamená můžete zadat pouze jeden základní třídu pro odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="de6ee-237">Chcete-li zdědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="de6ee-238">Ve výchozím nastavení může být dědí všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-238">By default all classes can be inherited.</span></span> <span data-ttu-id="de6ee-239">Však můžete určit, zda nesmí používat jako základní třída třídy, nebo vytvořte třídu, která lze použít jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="de6ee-240">Chcete-li určit, že třídy nelze použít jako základní třída:</span><span class="sxs-lookup"><span data-stu-id="de6ee-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="de6ee-241">K určení, že třídy lze použít jako základní třída a nelze vytvořit instanci:</span><span class="sxs-lookup"><span data-stu-id="de6ee-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="de6ee-242">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-242">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-243">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [<span data-ttu-id="de6ee-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="de6ee-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [<span data-ttu-id="de6ee-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="de6ee-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="de6ee-246">Přepis členů</span><span class="sxs-lookup"><span data-stu-id="de6ee-246">Overriding members</span></span>
<span data-ttu-id="de6ee-247">Ve výchozím nastavení odvozené třídy dědí všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="de6ee-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="de6ee-248">Pokud chcete změnit chování zděděného členu, budete muset přepsat.</span><span class="sxs-lookup"><span data-stu-id="de6ee-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="de6ee-249">To znamená můžete definovat nové implementace metoda, vlastnost nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="de6ee-250">Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="de6ee-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="de6ee-251">Modifikátor jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de6ee-251">Visual Basic Modifier</span></span>|<span data-ttu-id="de6ee-252">Definice</span><span class="sxs-lookup"><span data-stu-id="de6ee-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="de6ee-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="de6ee-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="de6ee-254">Umožňuje člena třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="de6ee-255">Přepsání</span><span class="sxs-lookup"><span data-stu-id="de6ee-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="de6ee-256">Přepsání člena virtuální (přepisovatelné) definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="de6ee-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="de6ee-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="de6ee-258">Zabrání přepsání dědičných třídy členem.</span><span class="sxs-lookup"><span data-stu-id="de6ee-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="de6ee-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="de6ee-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="de6ee-260">Vyžaduje, aby člena třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="de6ee-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="de6ee-261">Stínů</span><span class="sxs-lookup"><span data-stu-id="de6ee-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="de6ee-262">Skryje členem zděděn ze základní třídy</span><span class="sxs-lookup"><span data-stu-id="de6ee-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="de6ee-263">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6ee-263">Interfaces</span></span>
<span data-ttu-id="de6ee-264">Rozhraní, jako jsou třídy, definovat sadu vlastností, metod a události.</span><span class="sxs-lookup"><span data-stu-id="de6ee-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="de6ee-265">Ale na rozdíl od třídy, rozhraní neposkytují implementace.</span><span class="sxs-lookup"><span data-stu-id="de6ee-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="de6ee-266">Jsou implementované třídy a definován jako samostatné entity z tříd.</span><span class="sxs-lookup"><span data-stu-id="de6ee-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="de6ee-267">Rozhraní představuje kontraktu, v tomto třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.</span><span class="sxs-lookup"><span data-stu-id="de6ee-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="de6ee-268">Definice rozhraní:</span><span class="sxs-lookup"><span data-stu-id="de6ee-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="de6ee-269">K implementaci rozhraní v třídě:</span><span class="sxs-lookup"><span data-stu-id="de6ee-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="de6ee-270">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-270">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-271">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6ee-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [<span data-ttu-id="de6ee-272">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [<span data-ttu-id="de6ee-273">Implements – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a><span data-ttu-id="de6ee-274">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-274">Generics</span></span>
<span data-ttu-id="de6ee-275">Třídy, struktury, rozhraní a metody v rozhraní .NET může zahrnovat *parametry typu* , definování typů objektů, které lze uložit nebo použít.</span><span class="sxs-lookup"><span data-stu-id="de6ee-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="de6ee-276">Nejčastější obecných typů je kolekce, kde můžete určit typ objektů, které chcete uložit v kolekci.</span><span class="sxs-lookup"><span data-stu-id="de6ee-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  

<span data-ttu-id="de6ee-277">Zadat obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="de6ee-278">Chcete-li vytvořit instanci obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="de6ee-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="de6ee-279">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-279">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-280">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="de6ee-280">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="de6ee-281">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de6ee-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="de6ee-282">Delegáty</span><span class="sxs-lookup"><span data-stu-id="de6ee-282">Delegates</span></span>
 <span data-ttu-id="de6ee-283">A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu kompatibilní podpisem.</span><span class="sxs-lookup"><span data-stu-id="de6ee-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="de6ee-284">Můžete vyvolat (nebo volání) metoda prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="de6ee-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="de6ee-285">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="de6ee-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
>  <span data-ttu-id="de6ee-286">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="de6ee-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="de6ee-287">Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="de6ee-288">Pokud chcete vytvořit delegáta:</span><span class="sxs-lookup"><span data-stu-id="de6ee-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="de6ee-289">Pokud chcete vytvořit odkaz na metodu, která odpovídá podpis určeného delegát:</span><span class="sxs-lookup"><span data-stu-id="de6ee-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="de6ee-290">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="de6ee-290">For more information, see:</span></span>

- [<span data-ttu-id="de6ee-291">Delegáti</span><span class="sxs-lookup"><span data-stu-id="de6ee-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)

- [<span data-ttu-id="de6ee-292">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="de6ee-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="de6ee-293">AddressOf – operátor</span><span class="sxs-lookup"><span data-stu-id="de6ee-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="de6ee-294">Viz také</span><span class="sxs-lookup"><span data-stu-id="de6ee-294">See also</span></span>
 [<span data-ttu-id="de6ee-295">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de6ee-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
