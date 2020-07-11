---
title: Objektově orientované programování (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 83140a9dbd16f60f04f50ba18c71099cdd862f15
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226631"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="93191-102">Objektově orientované programování (C#)</span><span class="sxs-lookup"><span data-stu-id="93191-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="93191-103">Jazyk C# poskytuje úplnou podporu pro objektově orientované programování, včetně abstrakce, zapouzdření, dědičnosti a polymorfismu.</span><span class="sxs-lookup"><span data-stu-id="93191-103">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="93191-104">*Abstrakce* znamená skrývání zbytečných podrobností od spotřebitelů typu.</span><span class="sxs-lookup"><span data-stu-id="93191-104">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="93191-105">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="93191-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="93191-106">*Dědičnost* popisuje možnost vytvářet nové třídy na základě existující třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="93191-107">*Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelné, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="93191-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="93191-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="93191-108">Classes and objects</span></span>

<span data-ttu-id="93191-109">Výrazy *Třída* a *Object* popisují *typ* objektů a *instance* tříd, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="93191-109">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="93191-110">To znamená, že vytvoření objektu se nazývá vytváření *instancí*.</span><span class="sxs-lookup"><span data-stu-id="93191-110">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="93191-111">Pomocí analogie podrobného plánu je třída plán a objekt je sestaven z tohoto podrobného plánu.</span><span class="sxs-lookup"><span data-stu-id="93191-111">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="93191-112">Definování třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-112">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="93191-113">Jazyk C# také poskytuje typy označované jako *struktury* , které jsou užitečné, pokud nepotřebujete podporu dědičnosti nebo polymorfismu.</span><span class="sxs-lookup"><span data-stu-id="93191-113">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="93191-114">Další informace naleznete v tématu [Výběr mezi třídou a strukturou](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span><span class="sxs-lookup"><span data-stu-id="93191-114">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="93191-115">Definování struktury:</span><span class="sxs-lookup"><span data-stu-id="93191-115">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="93191-116">Další informace najdete v článcích o klíčových slovech [třídy](../../language-reference/keywords/class.md) a [struktury](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="93191-116">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="93191-117">Členové třídy</span><span class="sxs-lookup"><span data-stu-id="93191-117">Class members</span></span>

<span data-ttu-id="93191-118">Každá třída může mít různé *členy třídy* , které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy, a události, které poskytují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="93191-118">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="93191-119">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="93191-119">Properties and fields</span></span>

<span data-ttu-id="93191-120">Pole a vlastnosti reprezentují informace, které objekt obsahuje.</span><span class="sxs-lookup"><span data-stu-id="93191-120">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="93191-121">Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo v souladu s platnými modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="93191-121">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="93191-122">Chcete-li definovat pole, ke kterému lze přistupovat v rámci instancí třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-122">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="93191-123">Vlastnosti `get` a `set` přistupující objekty, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vraceny.</span><span class="sxs-lookup"><span data-stu-id="93191-123">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="93191-124">Jazyk C# umožňuje vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít automaticky implementované vlastnosti, které automaticky vytvoří toto pole na pozadí a poskytnou základní logiku pro procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="93191-124">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="93191-125">Definování automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="93191-125">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="93191-126">Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro uložení a načtení:</span><span class="sxs-lookup"><span data-stu-id="93191-126">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="93191-127">Většina vlastností má metody nebo postupy pro nastavení a získání hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="93191-127">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="93191-128">Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis a omezit tak jejich úpravu nebo čtení.</span><span class="sxs-lookup"><span data-stu-id="93191-128">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="93191-129">V jazyce C# můžete vynechat `get` `set` metodu nebo.</span><span class="sxs-lookup"><span data-stu-id="93191-129">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="93191-130">Automaticky implementované vlastnosti však nemohou být pouze pro zápis.</span><span class="sxs-lookup"><span data-stu-id="93191-130">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="93191-131">Automaticky implementované vlastnosti jen pro čtení lze nastavit v konstruktorech obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-131">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="93191-132">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="93191-132">For more information, see:</span></span>

- [<span data-ttu-id="93191-133">Čtěte</span><span class="sxs-lookup"><span data-stu-id="93191-133">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="93191-134">stanovenými</span><span class="sxs-lookup"><span data-stu-id="93191-134">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="93191-135">Metody</span><span class="sxs-lookup"><span data-stu-id="93191-135">Methods</span></span>

<span data-ttu-id="93191-136">*Metoda* je akce, kterou může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="93191-136">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="93191-137">Chcete-li definovat metodu třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-137">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="93191-138">Třída může mít několik implementací nebo *přetížení*stejné metody, která se liší v počtu parametrů nebo typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="93191-138">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="93191-139">Přetížení metody:</span><span class="sxs-lookup"><span data-stu-id="93191-139">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="93191-140">Ve většině případů deklarujete metodu v rámci definice třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-140">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="93191-141">Jazyk C# však podporuje také *metody rozšíření* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-141">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="93191-142">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="93191-142">For more information, see:</span></span>

- [<span data-ttu-id="93191-143">Metody</span><span class="sxs-lookup"><span data-stu-id="93191-143">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="93191-144">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="93191-144">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="93191-145">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="93191-145">Constructors</span></span>

<span data-ttu-id="93191-146">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="93191-146">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="93191-147">Konstruktory obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="93191-147">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="93191-148">Konstruktor lze spustit pouze jednou při vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-148">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="93191-149">Kromě toho kód v konstruktoru se vždy spouští před jakýmkoli jiným kódem ve třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-149">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="93191-150">Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoli jiné metody.</span><span class="sxs-lookup"><span data-stu-id="93191-150">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="93191-151">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="93191-151">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="93191-152">Další informace naleznete v tématu [konstruktory](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="93191-152">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="93191-153">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="93191-153">Finalizers</span></span>

<span data-ttu-id="93191-154">Finalizační metoda se používá k destrukci instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="93191-154">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="93191-155">V rozhraní .NET systém uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="93191-155">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="93191-156">Nicméně stále budete potřebovat finalizační metody k vyčištění všech nespravovaných prostředků, které vaše aplikace vytvoří.</span><span class="sxs-lookup"><span data-stu-id="93191-156">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="93191-157">Pro třídu může existovat pouze jeden finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="93191-157">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="93191-158">Další informace o finalizační a uvolňování paměti v rozhraní .NET najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="93191-158">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="93191-159">Události</span><span class="sxs-lookup"><span data-stu-id="93191-159">Events</span></span>

<span data-ttu-id="93191-160">Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu.</span><span class="sxs-lookup"><span data-stu-id="93191-160">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="93191-161">Třída, která odesílá (nebo vyvolává) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo zpracovávají) událost se nazývají *předplatitelé*.</span><span class="sxs-lookup"><span data-stu-id="93191-161">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="93191-162">Další informace o událostech, jak jsou vyvolány a zpracovávány, naleznete v tématu [events](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="93191-162">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="93191-163">Chcete-li deklarovat událost ve třídě, použijte klíčové slovo [Event](../../language-reference/keywords/event.md) .</span><span class="sxs-lookup"><span data-stu-id="93191-163">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="93191-164">Chcete-li vyvolat událost, vyvolejte delegáta události.</span><span class="sxs-lookup"><span data-stu-id="93191-164">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="93191-165">Chcete-li se přihlásit k odběru události, použijte `+=` operátor; Chcete-li zrušit odběr události, použijte `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="93191-165">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="93191-166">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="93191-166">Nested classes</span></span>

<span data-ttu-id="93191-167">Třída definovaná v rámci jiné třídy se nazývá *vnořená*.</span><span class="sxs-lookup"><span data-stu-id="93191-167">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="93191-168">Ve výchozím nastavení je vnořená třída soukromá.</span><span class="sxs-lookup"><span data-stu-id="93191-168">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="93191-169">Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a následně následovaný názvem vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-169">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="93191-170">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="93191-170">Access modifiers and access levels</span></span>

<span data-ttu-id="93191-171">Všechny třídy a členy třídy mohou určit, jakou úroveň přístupu poskytují jiné třídě, pomocí *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="93191-171">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="93191-172">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="93191-172">The following access modifiers are available:</span></span>

| <span data-ttu-id="93191-173">Modifikátor C#</span><span class="sxs-lookup"><span data-stu-id="93191-173">C# Modifier</span></span> | <span data-ttu-id="93191-174">Definice</span><span class="sxs-lookup"><span data-stu-id="93191-174">Definition</span></span> |
|--|--|
| [<span data-ttu-id="93191-175">public</span><span class="sxs-lookup"><span data-stu-id="93191-175">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="93191-176">Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="93191-176">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="93191-177">hlášen</span><span class="sxs-lookup"><span data-stu-id="93191-177">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="93191-178">Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-178">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="93191-179">protected</span><span class="sxs-lookup"><span data-stu-id="93191-179">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="93191-180">Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-180">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="93191-181">internal</span><span class="sxs-lookup"><span data-stu-id="93191-181">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="93191-182">K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="93191-182">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="93191-183">protected internal</span><span class="sxs-lookup"><span data-stu-id="93191-183">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="93191-184">K typu nebo členu může být přistup libovolným kódem ve stejném sestavení nebo libovolnou odvozenou třídou v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="93191-184">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="93191-185">private protected</span><span class="sxs-lookup"><span data-stu-id="93191-185">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="93191-186">Typ nebo člen je k dispozici v kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-186">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="93191-187">Další informace najdete v tématu [modifikátory přístupu](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="93191-187">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="93191-188">Vytváření instancí tříd</span><span class="sxs-lookup"><span data-stu-id="93191-188">Instantiating classes</span></span>

<span data-ttu-id="93191-189">Chcete-li vytvořit objekt, je nutné vytvořit instanci třídy nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-189">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="93191-190">Po vytvoření instance třídy můžete přiřadit hodnoty vlastnostem a polím instance a vyvolat metody třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-190">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="93191-191">Chcete-li přiřadit hodnoty vlastnostem během procesu vytváření instancí třídy, použijte Inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="93191-191">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="93191-192">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="93191-192">For more information, see:</span></span>

- [<span data-ttu-id="93191-193">New – operátor</span><span class="sxs-lookup"><span data-stu-id="93191-193">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="93191-194">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="93191-194">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="93191-195">Statické třídy a členy</span><span class="sxs-lookup"><span data-stu-id="93191-195">Static Classes and Members</span></span>

<span data-ttu-id="93191-196">Statický člen třídy je vlastnost, procedura nebo pole, které jsou sdíleny všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-196">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="93191-197">Definování statického člena:</span><span class="sxs-lookup"><span data-stu-id="93191-197">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="93191-198">Chcete-li získat přístup ke statickému členu, použijte název třídy bez vytvoření objektu této třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-198">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="93191-199">Statické třídy v jazyce C# mají pouze statické členy a nelze je vytvořit z instance.</span><span class="sxs-lookup"><span data-stu-id="93191-199">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="93191-200">Statické členy také nemají přístup k nestatickým vlastnostem, polím nebo metodám.</span><span class="sxs-lookup"><span data-stu-id="93191-200">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="93191-201">Další informace naleznete zde: [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="93191-201">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="93191-202">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="93191-202">Anonymous types</span></span>

<span data-ttu-id="93191-203">Anonymní typy umožňují vytvářet objekty bez psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="93191-203">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="93191-204">Místo toho kompilátor vygeneruje třídu za vás.</span><span class="sxs-lookup"><span data-stu-id="93191-204">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="93191-205">Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklaraci objektu.</span><span class="sxs-lookup"><span data-stu-id="93191-205">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="93191-206">Vytvoření instance anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="93191-206">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="93191-207">Další informace najdete v tématech: [anonymní typy](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="93191-207">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="93191-208">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="93191-208">Inheritance</span></span>

<span data-ttu-id="93191-209">Dědičnost umožňuje vytvořit novou třídu, která znovu používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-209">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="93191-210">Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*.</span><span class="sxs-lookup"><span data-stu-id="93191-210">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="93191-211">Nicméně všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídy, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-211">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="93191-212">Jazyk C# nepodporuje vícenásobnou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="93191-212">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="93191-213">To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="93191-213">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="93191-214">Chcete-li dědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-214">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="93191-215">Ve výchozím nastavení mohou být děděny všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-215">By default all classes can be inherited.</span></span> <span data-ttu-id="93191-216">Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, která může být použita pouze jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="93191-216">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="93191-217">Chcete-li určit, že třídu nelze použít jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="93191-217">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="93191-218">Chcete-li určit, že třída může být použita pouze jako základní třída a nemůže být vytvořena instance:</span><span class="sxs-lookup"><span data-stu-id="93191-218">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="93191-219">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="93191-219">For more information, see:</span></span>

- [<span data-ttu-id="93191-220">sealed</span><span class="sxs-lookup"><span data-stu-id="93191-220">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="93191-221">Výtah</span><span class="sxs-lookup"><span data-stu-id="93191-221">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="93191-222">Přepisování členů</span><span class="sxs-lookup"><span data-stu-id="93191-222">Overriding Members</span></span>

<span data-ttu-id="93191-223">Ve výchozím nastavení zdědí odvozená třída všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-223">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="93191-224">Pokud chcete změnit chování zděděného člena, je nutné ho přepsat.</span><span class="sxs-lookup"><span data-stu-id="93191-224">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="93191-225">To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-225">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="93191-226">Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:</span><span class="sxs-lookup"><span data-stu-id="93191-226">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="93191-227">Modifikátor C#</span><span class="sxs-lookup"><span data-stu-id="93191-227">C# Modifier</span></span> | <span data-ttu-id="93191-228">Definice</span><span class="sxs-lookup"><span data-stu-id="93191-228">Definition</span></span> |
|--|--|
| [<span data-ttu-id="93191-229">VM</span><span class="sxs-lookup"><span data-stu-id="93191-229">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="93191-230">Umožňuje přepsat člena třídy v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-230">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="93191-231">override</span><span class="sxs-lookup"><span data-stu-id="93191-231">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="93191-232">Přepíše virtuální (overridabled) člen definovaný v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-232">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="93191-233">Výtah</span><span class="sxs-lookup"><span data-stu-id="93191-233">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="93191-234">Vyžaduje, aby byl člen třídy přepsán v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="93191-234">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="93191-235">new – modifikátor</span><span class="sxs-lookup"><span data-stu-id="93191-235">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="93191-236">Skryje člena zděděného ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="93191-236">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="93191-237">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="93191-237">Interfaces</span></span>

<span data-ttu-id="93191-238">Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí.</span><span class="sxs-lookup"><span data-stu-id="93191-238">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="93191-239">Ale na rozdíl od tříd rozhraní neposkytuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="93191-239">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="93191-240">Jsou implementovány pomocí tříd a definovány jako samostatné entity ze tříd.</span><span class="sxs-lookup"><span data-stu-id="93191-240">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="93191-241">Rozhraní představuje kontrakt, v tom smyslu, že třída, která implementuje rozhraní, musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definováno.</span><span class="sxs-lookup"><span data-stu-id="93191-241">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="93191-242">Definování rozhraní:</span><span class="sxs-lookup"><span data-stu-id="93191-242">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="93191-243">Implementace rozhraní ve třídě:</span><span class="sxs-lookup"><span data-stu-id="93191-243">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="93191-244">Další informace najdete v článku Průvodce programováním v tématu [rozhraní](../interfaces/index.md) a referenční informace k jazyku na klíčovém slově [rozhraní](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="93191-244">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="93191-245">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="93191-245">Generics</span></span>

<span data-ttu-id="93191-246">Třídy, struktury, rozhraní a metody v rozhraní .NET mohou zahrnovat *parametry typu* , které definují typy objektů, které mohou ukládat nebo používat.</span><span class="sxs-lookup"><span data-stu-id="93191-246">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="93191-247">Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="93191-247">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="93191-248">Definování obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-248">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="93191-249">Vytvoření instance obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="93191-249">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="93191-250">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="93191-250">For more information, see:</span></span>

- [<span data-ttu-id="93191-251">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="93191-251">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="93191-252">Obecné typy – Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="93191-252">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="93191-253">Delegáti</span><span class="sxs-lookup"><span data-stu-id="93191-253">Delegates</span></span>

<span data-ttu-id="93191-254">*Delegát* je typ, který definuje signaturu metody a může poskytnout odkaz na libovolnou metodu s kompatibilní signaturou.</span><span class="sxs-lookup"><span data-stu-id="93191-254">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="93191-255">Metodu můžete vyvolat (nebo volat) prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="93191-255">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="93191-256">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="93191-256">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="93191-257">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="93191-257">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="93191-258">Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="93191-258">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="93191-259">Postup vytvoření delegáta:</span><span class="sxs-lookup"><span data-stu-id="93191-259">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="93191-260">Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu určenému delegátem:</span><span class="sxs-lookup"><span data-stu-id="93191-260">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
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

<span data-ttu-id="93191-261">Další informace najdete v článku Průvodce programováním u [delegátů](../delegates/index.md) a v článku referenční informace o jazyce na klíčovém slově [Delegate](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="93191-261">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="93191-262">Viz také</span><span class="sxs-lookup"><span data-stu-id="93191-262">See also</span></span>

- [<span data-ttu-id="93191-263">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="93191-263">C# Programming Guide</span></span>](../index.md)
