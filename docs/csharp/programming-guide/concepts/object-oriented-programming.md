---
title: Objektově orientované programování (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: a6194cb93b10d5b9f5d25fc42cff6c071627d411
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415485"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="95fc9-102">Objektově orientované programování (C#)</span><span class="sxs-lookup"><span data-stu-id="95fc9-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="95fc9-103">C# poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="95fc9-104">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="95fc9-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="95fc9-105">*Dědičnost* popisuje schopnost vytvářet nové třídy na základě existující třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="95fc9-106">*Polymorfismus* znamená, že můžete mít více tříd, které můžete používat Zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="95fc9-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="95fc9-107">Tato část popisuje následující pojmy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="95fc9-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="95fc9-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="95fc9-109">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="95fc9-110">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="95fc9-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="95fc9-111">Metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="95fc9-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="95fc9-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="95fc9-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="95fc9-114">Události</span><span class="sxs-lookup"><span data-stu-id="95fc9-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="95fc9-115">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="95fc9-116">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="95fc9-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="95fc9-117">Vytvoření instance třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="95fc9-118">Statické třídy a členové</span><span class="sxs-lookup"><span data-stu-id="95fc9-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="95fc9-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="95fc9-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="95fc9-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="95fc9-121">Obejití členů</span><span class="sxs-lookup"><span data-stu-id="95fc9-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="95fc9-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="95fc9-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="95fc9-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="95fc9-124">Delegáti</span><span class="sxs-lookup"><span data-stu-id="95fc9-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a> <span data-ttu-id="95fc9-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="95fc9-125">Classes and Objects</span></span>  
 <span data-ttu-id="95fc9-126">Podmínky *třídy* a *objekt* se někdy používají vzájemné záměně, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd.</span><span class="sxs-lookup"><span data-stu-id="95fc9-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="95fc9-127">Ano, je volána při vytvoření objektu *instance*.</span><span class="sxs-lookup"><span data-stu-id="95fc9-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="95fc9-128">Při použití analogie matric, třída je podrobný plán a objekt je vytvořen z této matrice budovy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="95fc9-129">Definování třídy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="95fc9-130">C# obsahuje také jednodušší verzi tříd pojmenovanou *struktury* , které jsou užitečné, když budete chtít vytvořit velké pole objektů a proveďte k tomu k tomu spotřebovat příliš mnoho paměti.</span><span class="sxs-lookup"><span data-stu-id="95fc9-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="95fc9-131">Definování struktury:</span><span class="sxs-lookup"><span data-stu-id="95fc9-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="95fc9-132">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-133">class</span><span class="sxs-lookup"><span data-stu-id="95fc9-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="95fc9-134">struct</span><span class="sxs-lookup"><span data-stu-id="95fc9-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> <span data-ttu-id="95fc9-135">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-135">Class Members</span></span>  
 <span data-ttu-id="95fc9-136">Každá třída může mít různé *členy třídy* obsahující vlastnosti, které popisují data třídy, metody, které určují chování třídy a události, které umožňují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="95fc9-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a> <span data-ttu-id="95fc9-137">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="95fc9-137">Properties and Fields</span></span>  
 <span data-ttu-id="95fc9-138">Pole a vlastnosti představují informace, které obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="95fc9-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="95fc9-139">Pole jsou jako proměnné, protože mohou být čtena nebo nastavena přímo.</span><span class="sxs-lookup"><span data-stu-id="95fc9-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="95fc9-140">Definování pole:</span><span class="sxs-lookup"><span data-stu-id="95fc9-140">To define a field:</span></span>  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="95fc9-141">Vlastnosti mají get a nastavte postupy, které poskytují větší kontrolu toho, jak jsou hodnoty nastavena nebo vrácena.</span><span class="sxs-lookup"><span data-stu-id="95fc9-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="95fc9-142">C# můžete buď vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí a poskytnou základní logiku pro procedury vlastností.</span><span class="sxs-lookup"><span data-stu-id="95fc9-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="95fc9-143">Chcete-li definovat automaticky implementovanou vlastnost:</span><span class="sxs-lookup"><span data-stu-id="95fc9-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="95fc9-144">Pokud je potřeba provést některé další operace čtení a zápisu hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro ukládání a načítání:</span><span class="sxs-lookup"><span data-stu-id="95fc9-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="95fc9-145">Většina vlastností má metody nebo postupy, jak nastavit a získat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95fc9-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="95fc9-146">Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, abyste omezili je číst nebo upravovat.</span><span class="sxs-lookup"><span data-stu-id="95fc9-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="95fc9-147">V jazyce C# můžete vynechat `get` nebo `set` metoda vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95fc9-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="95fc9-148">Automaticky implementované vlastnosti nemůže být ale jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="95fc9-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="95fc9-149">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-150">get</span><span class="sxs-lookup"><span data-stu-id="95fc9-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="95fc9-151">set</span><span class="sxs-lookup"><span data-stu-id="95fc9-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> <span data-ttu-id="95fc9-152">Metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-152">Methods</span></span>  
 <span data-ttu-id="95fc9-153">A *metoda* je akce, které může objekt provádět.</span><span class="sxs-lookup"><span data-stu-id="95fc9-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="95fc9-154">Chcete-li definovat metodu pro třídu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="95fc9-155">Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se liší v počtu parametrů nebo typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="95fc9-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="95fc9-156">Chcete-li přetížit metodu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="95fc9-157">Ve většině případů deklarujete metodu v rámci definice třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="95fc9-158">Ale jazyka C# také podporuje *rozšiřující metody* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="95fc9-159">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-160">Metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="95fc9-161">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> <span data-ttu-id="95fc9-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="95fc9-162">Constructors</span></span>  
 <span data-ttu-id="95fc9-163">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="95fc9-164">Konstruktory obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="95fc9-165">Konstruktor lze spustit pouze jednou při vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="95fc9-166">Kromě toho kód v konstruktoru se vždy spouští před ostatním kódem ve třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="95fc9-167">Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoliv jiné metody.</span><span class="sxs-lookup"><span data-stu-id="95fc9-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="95fc9-168">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="95fc9-169">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-169">For more information, see:</span></span>  
  
 <span data-ttu-id="95fc9-170">[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a> <span data-ttu-id="95fc9-171">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="95fc9-171">Finalizers</span></span>  
 <span data-ttu-id="95fc9-172">Finalizační metody se používají k destrukci instancí tříd.</span><span class="sxs-lookup"><span data-stu-id="95fc9-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="95fc9-173">V rozhraní .NET Framework systému uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="95fc9-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="95fc9-174">Může však stále zapotřebí finalizační metody pro vyčištění všech nespravovaných prostředků, které vytváří vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="95fc9-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="95fc9-175">Může existovat pouze jeden finalizační metody pro třídu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="95fc9-176">Další informace o finalizační metody a systém kolekce paměti v rozhraní .NET Framework najdete v tématu [uvolňování](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a> <span data-ttu-id="95fc9-177">Události</span><span class="sxs-lookup"><span data-stu-id="95fc9-177">Events</span></span>  
 <span data-ttu-id="95fc9-178">Události umožňují třídám nebo objektům upozornit ostatní třídy nebo objekty, když něco, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="95fc9-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="95fc9-179">Třída, která odesílá (nebo vyvolává) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *předplatitele*.</span><span class="sxs-lookup"><span data-stu-id="95fc9-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="95fc9-180">Další informace o událostech, jak jejich vyvolávání a zpracování viz [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="95fc9-181">Chcete-li deklarovat událost v třídě, použijte [události](../../../csharp/language-reference/keywords/event.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="95fc9-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="95fc9-182">K vyvolání události vyvolejte delegáta události.</span><span class="sxs-lookup"><span data-stu-id="95fc9-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="95fc9-183">Chcete-li přihlásit odběr události, použijte `+=` operátor; Chcete-li zrušit odběr události, použijte `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="95fc9-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a> <span data-ttu-id="95fc9-184">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-184">Nested Classes</span></span>  
 <span data-ttu-id="95fc9-185">Třída definována v rámci jiné třídy se nazývá *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="95fc9-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="95fc9-186">Ve výchozím nastavení vnořené třídy je privátní.</span><span class="sxs-lookup"><span data-stu-id="95fc9-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="95fc9-187">Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaného tečkou a pak následovaného názvem vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> <span data-ttu-id="95fc9-188">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="95fc9-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="95fc9-189">Všechny třídy a členy třídy můžete určit úroveň přístupu poskytují dalším třídám, pomocí *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="95fc9-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="95fc9-190">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="95fc9-191">Modifikátor C#</span><span class="sxs-lookup"><span data-stu-id="95fc9-191">C# Modifier</span></span>|<span data-ttu-id="95fc9-192">Definice</span><span class="sxs-lookup"><span data-stu-id="95fc9-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="95fc9-193">public</span><span class="sxs-lookup"><span data-stu-id="95fc9-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="95fc9-194">Tento typ nebo člen je přístupný libovolnému jinému kódu ve stejném sestavení nebo libovolnému sestavení která na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="95fc9-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="95fc9-195">private</span><span class="sxs-lookup"><span data-stu-id="95fc9-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="95fc9-196">Tento typ nebo člen je přístupný pouze kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="95fc9-197">protected</span><span class="sxs-lookup"><span data-stu-id="95fc9-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="95fc9-198">Tento typ nebo člen je přístupný pouze kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="95fc9-199">internal</span><span class="sxs-lookup"><span data-stu-id="95fc9-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="95fc9-200">Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, ale ne z jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="95fc9-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="95fc9-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="95fc9-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="95fc9-202">Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, nebo kterékoli odvozené třídě v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="95fc9-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="95fc9-203">private protected</span><span class="sxs-lookup"><span data-stu-id="95fc9-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="95fc9-204">Tento typ nebo člen je přístupný pomocí kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="95fc9-205">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a> <span data-ttu-id="95fc9-206">Vytvoření instance třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-206">Instantiating Classes</span></span>  
 <span data-ttu-id="95fc9-207">Pro vytvoření objektu, budete muset vytvořit instanci třídy, nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="95fc9-208">Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a volat metody třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="95fc9-209">Chcete-li přiřadit hodnoty vlastností během procesu vytváření instance třídy, použijte inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="95fc9-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="95fc9-210">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-211">new – operátor</span><span class="sxs-lookup"><span data-stu-id="95fc9-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="95fc9-212">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="95fc9-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> <span data-ttu-id="95fc9-213">Statické třídy a členové</span><span class="sxs-lookup"><span data-stu-id="95fc9-213">Static Classes and Members</span></span>  
 <span data-ttu-id="95fc9-214">Statický člen třídy je vlastnost, procedura nebo pole, která je sdílena všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="95fc9-215">Chcete-li definovat statický člen:</span><span class="sxs-lookup"><span data-stu-id="95fc9-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="95fc9-216">Pro přístup k statický člen, použijte název třídy bez vytvoření objektů této třídy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="95fc9-217">Statické třídy v jazyce C# mít jenom statické členy a nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="95fc9-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="95fc9-218">Statické členy také nelze přistupovat k vlastnosti nestatické, polím nebo metodám</span><span class="sxs-lookup"><span data-stu-id="95fc9-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="95fc9-219">Další informace najdete v tématu: [statické](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a> <span data-ttu-id="95fc9-220">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-220">Anonymous Types</span></span>  
 <span data-ttu-id="95fc9-221">Anonymní typy umožňují vytvářet objekty bez psaní definice třídy datového typu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="95fc9-222">Místo toho kompilátor vygeneruje třídu za vás.</span><span class="sxs-lookup"><span data-stu-id="95fc9-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="95fc9-223">Třída nemá žádný použitelný název a obsahuje vlastnosti, které jste zadali v rámci deklarace objektu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="95fc9-224">Chcete-li vytvořit instanci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="95fc9-225">Další informace najdete v tématu: [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a> <span data-ttu-id="95fc9-226">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="95fc9-226">Inheritance</span></span>  
 <span data-ttu-id="95fc9-227">Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="95fc9-228">Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*, a názvem třídy, která dědí tyto členy *odvozené třídy*.</span><span class="sxs-lookup"><span data-stu-id="95fc9-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="95fc9-229">Nicméně všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně všem třídám.</span><span class="sxs-lookup"><span data-stu-id="95fc9-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95fc9-230">C# nepodporuje vícenásobnou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="95fc9-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="95fc9-231">To znamená můžete zadat pouze jednu základní třídu pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="95fc9-232">Chcete-li dědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 <span data-ttu-id="95fc9-233">Ve výchozím nastavení je možné zdědit všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-233">By default all classes can be inherited.</span></span> <span data-ttu-id="95fc9-234">Můžete však určit, zda třída nesmí používat jako základní třída nebo vytvořit třídu, která lze použít jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="95fc9-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="95fc9-235">Chcete-li určit, že třídu nelze použít jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="95fc9-236">Určíte, že třída může sloužit jako základní třídu a nelze vytvořit instanci:</span><span class="sxs-lookup"><span data-stu-id="95fc9-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="95fc9-237">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-238">sealed</span><span class="sxs-lookup"><span data-stu-id="95fc9-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="95fc9-239">abstract</span><span class="sxs-lookup"><span data-stu-id="95fc9-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> <span data-ttu-id="95fc9-240">Obejití členů</span><span class="sxs-lookup"><span data-stu-id="95fc9-240">Overriding Members</span></span>  
 <span data-ttu-id="95fc9-241">Ve výchozím nastavení dědí odvozená třída všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="95fc9-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="95fc9-242">Pokud chcete změnit chování zděděného člena, musíte ho potlačit.</span><span class="sxs-lookup"><span data-stu-id="95fc9-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="95fc9-243">To znamená můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="95fc9-244">Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="95fc9-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="95fc9-245">Modifikátor C#</span><span class="sxs-lookup"><span data-stu-id="95fc9-245">C# Modifier</span></span>|<span data-ttu-id="95fc9-246">Definice</span><span class="sxs-lookup"><span data-stu-id="95fc9-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="95fc9-247">virtual</span><span class="sxs-lookup"><span data-stu-id="95fc9-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="95fc9-248">Umožňuje člen třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="95fc9-249">override</span><span class="sxs-lookup"><span data-stu-id="95fc9-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="95fc9-250">Přepsání virtuální (s možností přepsání) člena definovaného v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="95fc9-251">abstract</span><span class="sxs-lookup"><span data-stu-id="95fc9-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="95fc9-252">Vyžaduje, aby člen třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="95fc9-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="95fc9-253">new – modifikátor</span><span class="sxs-lookup"><span data-stu-id="95fc9-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="95fc9-254">Skryje člena zděděného ze základní třídy</span><span class="sxs-lookup"><span data-stu-id="95fc9-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a> <span data-ttu-id="95fc9-255">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="95fc9-255">Interfaces</span></span>  
 <span data-ttu-id="95fc9-256">Rozhraní, stejně jako třídy, definují sadu vlastností, metody a události.</span><span class="sxs-lookup"><span data-stu-id="95fc9-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="95fc9-257">Ale na rozdíl od tříd, rozhraní neposkytují implementace.</span><span class="sxs-lookup"><span data-stu-id="95fc9-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="95fc9-258">Jsou implementované třídami a definovány jako samostatné subjekty ze tříd.</span><span class="sxs-lookup"><span data-stu-id="95fc9-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="95fc9-259">Rozhraní představuje smlouvu v tom, že třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.</span><span class="sxs-lookup"><span data-stu-id="95fc9-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="95fc9-260">Definování rozhraní:</span><span class="sxs-lookup"><span data-stu-id="95fc9-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="95fc9-261">Pro implementaci rozhraní ve třídě:</span><span class="sxs-lookup"><span data-stu-id="95fc9-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="95fc9-262">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="95fc9-263">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="95fc9-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="95fc9-264">interface</span><span class="sxs-lookup"><span data-stu-id="95fc9-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> <span data-ttu-id="95fc9-265">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-265">Generics</span></span>  
 <span data-ttu-id="95fc9-266">Třídy, struktury, rozhraní a metody v rozhraní .NET Framework může zahrnovat *parametry typu* , které definují typy objektů, které lze uložit nebo použít.</span><span class="sxs-lookup"><span data-stu-id="95fc9-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="95fc9-267">Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektu, který bude uložen do kolekce.</span><span class="sxs-lookup"><span data-stu-id="95fc9-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="95fc9-268">Chcete-li definovat obecnou třídu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-268">To define a generic class:</span></span>  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="95fc9-269">Vytvoření instance generické třídy:</span><span class="sxs-lookup"><span data-stu-id="95fc9-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="95fc9-270">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-271">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="95fc9-272">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="95fc9-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> <span data-ttu-id="95fc9-273">Delegáti</span><span class="sxs-lookup"><span data-stu-id="95fc9-273">Delegates</span></span>  
 <span data-ttu-id="95fc9-274">A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na jakoukoli metodu s kompatibilním podpisem.</span><span class="sxs-lookup"><span data-stu-id="95fc9-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="95fc9-275">Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="95fc9-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="95fc9-276">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="95fc9-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95fc9-277">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="95fc9-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="95fc9-278">Další informace o použití delegátů při zpracování událostí naleznete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="95fc9-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="95fc9-279">K vytvoření delegáta:</span><span class="sxs-lookup"><span data-stu-id="95fc9-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="95fc9-280">Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu zadanému delegátem:</span><span class="sxs-lookup"><span data-stu-id="95fc9-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="95fc9-281">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="95fc9-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="95fc9-282">Delegáti</span><span class="sxs-lookup"><span data-stu-id="95fc9-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="95fc9-283">delegate</span><span class="sxs-lookup"><span data-stu-id="95fc9-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="95fc9-284">Viz také</span><span class="sxs-lookup"><span data-stu-id="95fc9-284">See Also</span></span>  
 [<span data-ttu-id="95fc9-285">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="95fc9-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
