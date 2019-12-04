---
title: Objektově orientované programování (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 1de150f6eb4be893ca1afce6bd16afde5752c986
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711824"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="ebb62-102">Objektově orientované programování (C#)</span><span class="sxs-lookup"><span data-stu-id="ebb62-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="ebb62-103">C#poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="ebb62-104">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="ebb62-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="ebb62-105">*Dědičnost* popisuje možnost vytvářet nové třídy na základě existující třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="ebb62-106">*Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelné, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ebb62-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="ebb62-107">Tato část popisuje následující koncepty:</span><span class="sxs-lookup"><span data-stu-id="ebb62-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="ebb62-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="ebb62-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="ebb62-109">Členové třídy</span><span class="sxs-lookup"><span data-stu-id="ebb62-109">Class Members</span></span>](#Members)

    - [<span data-ttu-id="ebb62-110">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="ebb62-110">Properties and Fields</span></span>](#Properties)

    - [<span data-ttu-id="ebb62-111">Metody</span><span class="sxs-lookup"><span data-stu-id="ebb62-111">Methods</span></span>](#Methods)

    - [<span data-ttu-id="ebb62-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ebb62-112">Constructors</span></span>](#Constructors)

    - [<span data-ttu-id="ebb62-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ebb62-113">Finalizers</span></span>](#Finalizers)

    - [<span data-ttu-id="ebb62-114">Události</span><span class="sxs-lookup"><span data-stu-id="ebb62-114">Events</span></span>](#Events)

    - [<span data-ttu-id="ebb62-115">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="ebb62-115">Nested Classes</span></span>](#NestedClasses)

  - [<span data-ttu-id="ebb62-116">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="ebb62-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="ebb62-117">Vytváření instancí tříd</span><span class="sxs-lookup"><span data-stu-id="ebb62-117">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="ebb62-118">Statické třídy a členy</span><span class="sxs-lookup"><span data-stu-id="ebb62-118">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="ebb62-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-119">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="ebb62-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ebb62-120">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="ebb62-121">Přepisování členů</span><span class="sxs-lookup"><span data-stu-id="ebb62-121">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="ebb62-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebb62-122">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="ebb62-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-123">Generics</span></span>](#Generics)

- [<span data-ttu-id="ebb62-124">Delegáty</span><span class="sxs-lookup"><span data-stu-id="ebb62-124">Delegates</span></span>](#Delegates)

## <a name="Classes"></a><span data-ttu-id="ebb62-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="ebb62-125">Classes and Objects</span></span>

<span data-ttu-id="ebb62-126">*Třída* terms a *Object* se někdy používají zaměnitelné, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné *instance* tříd.</span><span class="sxs-lookup"><span data-stu-id="ebb62-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="ebb62-127">To znamená, že vytvoření objektu se nazývá vytváření *instancí*.</span><span class="sxs-lookup"><span data-stu-id="ebb62-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="ebb62-128">Pomocí analogie podrobného plánu je třída plán a objekt je sestaven z tohoto podrobného plánu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="ebb62-129">Definování třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-129">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="ebb62-130">C#poskytuje také světlou verzi tříd nazvaných *struktury* , které jsou užitečné v případě, že potřebujete vytvořit velké pole objektů a nechcete pro ně spotřebovat příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="ebb62-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="ebb62-131">Definování struktury:</span><span class="sxs-lookup"><span data-stu-id="ebb62-131">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="ebb62-132">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-132">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-133">class</span><span class="sxs-lookup"><span data-stu-id="ebb62-133">class</span></span>](../../language-reference/keywords/class.md)

- [<span data-ttu-id="ebb62-134">struct</span><span class="sxs-lookup"><span data-stu-id="ebb62-134">struct</span></span>](../../language-reference/keywords/struct.md)

### <a name="Members"></a><span data-ttu-id="ebb62-135">Členové třídy</span><span class="sxs-lookup"><span data-stu-id="ebb62-135">Class Members</span></span>

<span data-ttu-id="ebb62-136">Každá třída může mít různé *členy třídy* , které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy, a události, které poskytují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="ebb62-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a><span data-ttu-id="ebb62-137">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="ebb62-137">Properties and Fields</span></span>

<span data-ttu-id="ebb62-138">Pole a vlastnosti reprezentují informace, které objekt obsahuje.</span><span class="sxs-lookup"><span data-stu-id="ebb62-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="ebb62-139">Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo.</span><span class="sxs-lookup"><span data-stu-id="ebb62-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="ebb62-140">Definování pole:</span><span class="sxs-lookup"><span data-stu-id="ebb62-140">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="ebb62-141">Vlastnosti mají procedury Get a set, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vraceny.</span><span class="sxs-lookup"><span data-stu-id="ebb62-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="ebb62-142">C#umožňuje vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít automaticky implementované vlastnosti, které vytváří toto pole automaticky na pozadí a poskytuje základní logiku pro procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="ebb62-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="ebb62-143">Definování automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ebb62-143">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="ebb62-144">Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro uložení a načtení:</span><span class="sxs-lookup"><span data-stu-id="ebb62-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

<span data-ttu-id="ebb62-145">Většina vlastností má metody nebo postupy pro nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ebb62-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="ebb62-146">Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis a omezit tak jejich úpravu nebo čtení.</span><span class="sxs-lookup"><span data-stu-id="ebb62-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="ebb62-147">V C#nástroji můžete vynechat metodu vlastnosti `get` nebo `set`.</span><span class="sxs-lookup"><span data-stu-id="ebb62-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="ebb62-148">Automaticky implementované vlastnosti ale nemůžou být jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="ebb62-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="ebb62-149">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-149">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-150">get</span><span class="sxs-lookup"><span data-stu-id="ebb62-150">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="ebb62-151">set</span><span class="sxs-lookup"><span data-stu-id="ebb62-151">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="Methods"></a><span data-ttu-id="ebb62-152">Způsobů</span><span class="sxs-lookup"><span data-stu-id="ebb62-152">Methods</span></span>

<span data-ttu-id="ebb62-153">*Metoda* je akce, kterou může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="ebb62-153">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="ebb62-154">Chcete-li definovat metodu třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-154">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="ebb62-155">Třída může mít několik implementací nebo *přetížení*stejné metody, která se liší v počtu parametrů nebo typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="ebb62-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="ebb62-156">Přetížení metody:</span><span class="sxs-lookup"><span data-stu-id="ebb62-156">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="ebb62-157">Ve většině případů deklarujete metodu v rámci definice třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="ebb62-158">Nicméně podporuje C# také *metody rozšíření* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="ebb62-159">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-159">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-160">Metody</span><span class="sxs-lookup"><span data-stu-id="ebb62-160">Methods</span></span>](../classes-and-structs/methods.md)

- [<span data-ttu-id="ebb62-161">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="ebb62-161">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a><span data-ttu-id="ebb62-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ebb62-162">Constructors</span></span>

<span data-ttu-id="ebb62-163">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="ebb62-164">Konstruktory obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="ebb62-165">Konstruktor lze spustit pouze jednou při vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="ebb62-166">Kromě toho kód v konstruktoru se vždy spouští před jakýmkoli jiným kódem ve třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="ebb62-167">Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoli jiné metody.</span><span class="sxs-lookup"><span data-stu-id="ebb62-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="ebb62-168">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="ebb62-168">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="ebb62-169">Další informace naleznete v tématu [konstruktory](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-169">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a><span data-ttu-id="ebb62-170">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ebb62-170">Finalizers</span></span>

<span data-ttu-id="ebb62-171">Finalizační metody slouží k destrukci instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="ebb62-171">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="ebb62-172">V .NET Framework systém uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ebb62-172">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="ebb62-173">Nicméně stále budete potřebovat finalizační metody k vyčištění všech nespravovaných prostředků, které vaše aplikace vytvoří.</span><span class="sxs-lookup"><span data-stu-id="ebb62-173">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="ebb62-174">Pro třídu může existovat pouze jeden finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="ebb62-174">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="ebb62-175">Další informace o finalizační a uvolňování paměti v .NET Framework naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-175">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a><span data-ttu-id="ebb62-176">Událost</span><span class="sxs-lookup"><span data-stu-id="ebb62-176">Events</span></span>

<span data-ttu-id="ebb62-177">Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-177">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="ebb62-178">Třída, která odesílá (nebo vyvolává) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo zpracovávají) událost se nazývají *předplatitelé*.</span><span class="sxs-lookup"><span data-stu-id="ebb62-178">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="ebb62-179">Další informace o událostech, jak jsou vyvolány a zpracovávány, naleznete v tématu [events](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-179">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="ebb62-180">Chcete-li deklarovat událost ve třídě, použijte klíčové slovo [Event](../../language-reference/keywords/event.md) .</span><span class="sxs-lookup"><span data-stu-id="ebb62-180">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="ebb62-181">Chcete-li vyvolat událost, vyvolejte delegáta události.</span><span class="sxs-lookup"><span data-stu-id="ebb62-181">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="ebb62-182">K přihlášení k odběru události použijte operátor `+=`; Chcete-li zrušit odběr události, použijte operátor `-=`.</span><span class="sxs-lookup"><span data-stu-id="ebb62-182">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a><span data-ttu-id="ebb62-183">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="ebb62-183">Nested Classes</span></span>

<span data-ttu-id="ebb62-184">Třída definovaná v rámci jiné třídy se nazývá *vnořená*.</span><span class="sxs-lookup"><span data-stu-id="ebb62-184">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="ebb62-185">Ve výchozím nastavení je vnořená třída soukromá.</span><span class="sxs-lookup"><span data-stu-id="ebb62-185">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="ebb62-186">Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a následně následovaný názvem vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-186">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a><span data-ttu-id="ebb62-187">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="ebb62-187">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="ebb62-188">Všechny třídy a členy třídy mohou určit, jakou úroveň přístupu poskytují jiné třídě, pomocí *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="ebb62-188">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="ebb62-189">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="ebb62-189">The following access modifiers are available:</span></span>

|<span data-ttu-id="ebb62-190">C#Upravující</span><span class="sxs-lookup"><span data-stu-id="ebb62-190">C# Modifier</span></span>|<span data-ttu-id="ebb62-191">Definice</span><span class="sxs-lookup"><span data-stu-id="ebb62-191">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="ebb62-192">public</span><span class="sxs-lookup"><span data-stu-id="ebb62-192">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="ebb62-193">Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ebb62-193">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="ebb62-194">private</span><span class="sxs-lookup"><span data-stu-id="ebb62-194">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="ebb62-195">Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-195">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="ebb62-196">protected</span><span class="sxs-lookup"><span data-stu-id="ebb62-196">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="ebb62-197">Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-197">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="ebb62-198">internal</span><span class="sxs-lookup"><span data-stu-id="ebb62-198">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="ebb62-199">K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebb62-199">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="ebb62-200">protected internal</span><span class="sxs-lookup"><span data-stu-id="ebb62-200">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="ebb62-201">K typu nebo členu může být přistup libovolným kódem ve stejném sestavení nebo libovolnou odvozenou třídou v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebb62-201">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="ebb62-202">private protected</span><span class="sxs-lookup"><span data-stu-id="ebb62-202">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="ebb62-203">Typ nebo člen je k dispozici v kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-203">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="ebb62-204">Další informace najdete v tématu [modifikátory přístupu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-204">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a><span data-ttu-id="ebb62-205">Vytváření instancí tříd</span><span class="sxs-lookup"><span data-stu-id="ebb62-205">Instantiating Classes</span></span>

<span data-ttu-id="ebb62-206">Chcete-li vytvořit objekt, je nutné vytvořit instanci třídy nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-206">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="ebb62-207">Po vytvoření instance třídy můžete přiřadit hodnoty vlastnostem a polím instance a vyvolat metody třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-207">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="ebb62-208">Chcete-li přiřadit hodnoty vlastnostem během procesu vytváření instancí třídy, použijte Inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="ebb62-208">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="ebb62-209">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-209">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-210">new – operátor</span><span class="sxs-lookup"><span data-stu-id="ebb62-210">new Operator</span></span>](../../language-reference/operators/new-operator.md)

- [<span data-ttu-id="ebb62-211">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="ebb62-211">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a><span data-ttu-id="ebb62-212">Statické třídy a členy</span><span class="sxs-lookup"><span data-stu-id="ebb62-212">Static Classes and Members</span></span>

<span data-ttu-id="ebb62-213">Statický člen třídy je vlastnost, procedura nebo pole, které jsou sdíleny všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-213">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="ebb62-214">Definování statického člena:</span><span class="sxs-lookup"><span data-stu-id="ebb62-214">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="ebb62-215">Chcete-li získat přístup ke statickému členu, použijte název třídy bez vytvoření objektu této třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-215">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="ebb62-216">Statické třídy v C# mají pouze statické členy a nelze je vytvořit z instance.</span><span class="sxs-lookup"><span data-stu-id="ebb62-216">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="ebb62-217">Statické členy také nemají přístup k nestatickým vlastnostem, polím nebo metodám.</span><span class="sxs-lookup"><span data-stu-id="ebb62-217">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="ebb62-218">Další informace naleznete zde: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-218">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a><span data-ttu-id="ebb62-219">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-219">Anonymous Types</span></span>

<span data-ttu-id="ebb62-220">Anonymní typy umožňují vytvářet objekty bez psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="ebb62-220">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="ebb62-221">Místo toho kompilátor vygeneruje třídu za vás.</span><span class="sxs-lookup"><span data-stu-id="ebb62-221">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="ebb62-222">Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklaraci objektu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-222">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="ebb62-223">Vytvoření instance anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="ebb62-223">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="ebb62-224">Další informace najdete v tématech: [anonymní typy](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-224">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a><span data-ttu-id="ebb62-225">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ebb62-225">Inheritance</span></span>

<span data-ttu-id="ebb62-226">Dědičnost umožňuje vytvořit novou třídu, která znovu používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-226">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="ebb62-227">Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*.</span><span class="sxs-lookup"><span data-stu-id="ebb62-227">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="ebb62-228">Nicméně všechny třídy v C# implicitně dědí z třídy <xref:System.Object>, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-228">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="ebb62-229">C#nepodporuje vícenásobnou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="ebb62-229">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="ebb62-230">To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="ebb62-230">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="ebb62-231">Chcete-li dědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-231">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="ebb62-232">Ve výchozím nastavení mohou být děděny všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-232">By default all classes can be inherited.</span></span> <span data-ttu-id="ebb62-233">Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, která může být použita pouze jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="ebb62-233">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="ebb62-234">Chcete-li určit, že třídu nelze použít jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="ebb62-234">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="ebb62-235">Chcete-li určit, že třída může být použita pouze jako základní třída a nemůže být vytvořena instance:</span><span class="sxs-lookup"><span data-stu-id="ebb62-235">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="ebb62-236">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-236">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-237">sealed</span><span class="sxs-lookup"><span data-stu-id="ebb62-237">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="ebb62-238">abstract</span><span class="sxs-lookup"><span data-stu-id="ebb62-238">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a><span data-ttu-id="ebb62-239">Přepisování členů</span><span class="sxs-lookup"><span data-stu-id="ebb62-239">Overriding Members</span></span>

<span data-ttu-id="ebb62-240">Ve výchozím nastavení zdědí odvozená třída všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-240">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="ebb62-241">Pokud chcete změnit chování zděděného člena, je nutné ho přepsat.</span><span class="sxs-lookup"><span data-stu-id="ebb62-241">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="ebb62-242">To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-242">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="ebb62-243">Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:</span><span class="sxs-lookup"><span data-stu-id="ebb62-243">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="ebb62-244">C#Upravující</span><span class="sxs-lookup"><span data-stu-id="ebb62-244">C# Modifier</span></span>|<span data-ttu-id="ebb62-245">Definice</span><span class="sxs-lookup"><span data-stu-id="ebb62-245">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="ebb62-246">virtual</span><span class="sxs-lookup"><span data-stu-id="ebb62-246">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="ebb62-247">Umožňuje přepsat člena třídy v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-247">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="ebb62-248">override</span><span class="sxs-lookup"><span data-stu-id="ebb62-248">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="ebb62-249">Přepíše virtuální (overridabled) člen definovaný v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-249">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="ebb62-250">abstract</span><span class="sxs-lookup"><span data-stu-id="ebb62-250">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="ebb62-251">Vyžaduje, aby byl člen třídy přepsán v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ebb62-251">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="ebb62-252">new – modifikátor</span><span class="sxs-lookup"><span data-stu-id="ebb62-252">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="ebb62-253">Skryje člena zděděného ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ebb62-253">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a><span data-ttu-id="ebb62-254">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ebb62-254">Interfaces</span></span>

<span data-ttu-id="ebb62-255">Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí.</span><span class="sxs-lookup"><span data-stu-id="ebb62-255">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="ebb62-256">Ale na rozdíl od tříd rozhraní neposkytuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="ebb62-256">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="ebb62-257">Jsou implementovány pomocí tříd a definovány jako samostatné entity ze tříd.</span><span class="sxs-lookup"><span data-stu-id="ebb62-257">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="ebb62-258">Rozhraní představuje kontrakt, v tom smyslu, že třída, která implementuje rozhraní, musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definováno.</span><span class="sxs-lookup"><span data-stu-id="ebb62-258">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="ebb62-259">Definování rozhraní:</span><span class="sxs-lookup"><span data-stu-id="ebb62-259">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="ebb62-260">Implementace rozhraní ve třídě:</span><span class="sxs-lookup"><span data-stu-id="ebb62-260">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="ebb62-261">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-261">For more information, see:</span></span>

[<span data-ttu-id="ebb62-262">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebb62-262">Interfaces</span></span>](../interfaces/index.md)

[<span data-ttu-id="ebb62-263">interface</span><span class="sxs-lookup"><span data-stu-id="ebb62-263">interface</span></span>](../../language-reference/keywords/interface.md)

## <a name="Generics"></a><span data-ttu-id="ebb62-264">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-264">Generics</span></span>

<span data-ttu-id="ebb62-265">Třídy, struktury, rozhraní a metody v .NET Framework mohou zahrnovat *parametry typu* , které definují typy objektů, které mohou ukládat nebo používat.</span><span class="sxs-lookup"><span data-stu-id="ebb62-265">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="ebb62-266">Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ebb62-266">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="ebb62-267">Definování obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-267">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="ebb62-268">Vytvoření instance obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="ebb62-268">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="ebb62-269">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-269">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-270">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-270">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="ebb62-271">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ebb62-271">Generics</span></span>](../generics/index.md)

## <a name="Delegates"></a><span data-ttu-id="ebb62-272">Deleguje</span><span class="sxs-lookup"><span data-stu-id="ebb62-272">Delegates</span></span>

<span data-ttu-id="ebb62-273">*Delegát* je typ, který definuje signaturu metody a může poskytnout odkaz na libovolnou metodu s kompatibilní signaturou.</span><span class="sxs-lookup"><span data-stu-id="ebb62-273">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="ebb62-274">Metodu můžete vyvolat (nebo volat) prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="ebb62-274">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="ebb62-275">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="ebb62-275">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="ebb62-276">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="ebb62-276">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ebb62-277">Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebb62-277">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="ebb62-278">Postup vytvoření delegáta:</span><span class="sxs-lookup"><span data-stu-id="ebb62-278">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="ebb62-279">Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu určenému delegátem:</span><span class="sxs-lookup"><span data-stu-id="ebb62-279">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="ebb62-280">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="ebb62-280">For more information, see:</span></span>

- [<span data-ttu-id="ebb62-281">Delegáty</span><span class="sxs-lookup"><span data-stu-id="ebb62-281">Delegates</span></span>](../delegates/index.md)

- [<span data-ttu-id="ebb62-282">delegate</span><span class="sxs-lookup"><span data-stu-id="ebb62-282">delegate</span></span>](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="ebb62-283">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebb62-283">See also</span></span>

- [<span data-ttu-id="ebb62-284">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ebb62-284">C# Programming Guide</span></span>](../index.md)
