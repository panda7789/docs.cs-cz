---
title: "Objektově orientované programování (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a7f30293bb2d50981353badfb7e373b60dcfeec
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="70ebc-102">Objektově orientované programování (C#)</span><span class="sxs-lookup"><span data-stu-id="70ebc-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="70ebc-103">C# poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnost a polymorfismus.</span><span class="sxs-lookup"><span data-stu-id="70ebc-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="70ebc-104">*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="70ebc-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="70ebc-105">*Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="70ebc-106">*Polymorfismus* znamená, že můžete mít více tříd, které lze použít zcela zaměnitelným významem, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="70ebc-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="70ebc-107">Tato část popisuje následující koncepty:</span><span class="sxs-lookup"><span data-stu-id="70ebc-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="70ebc-108">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="70ebc-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="70ebc-109">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="70ebc-110">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="70ebc-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="70ebc-111">Metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="70ebc-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="70ebc-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="70ebc-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="70ebc-114">Události</span><span class="sxs-lookup"><span data-stu-id="70ebc-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="70ebc-115">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="70ebc-116">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="70ebc-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="70ebc-117">Vytváření instancí třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="70ebc-118">Statické třídy a členové</span><span class="sxs-lookup"><span data-stu-id="70ebc-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="70ebc-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="70ebc-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="70ebc-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="70ebc-121">Přepis členů</span><span class="sxs-lookup"><span data-stu-id="70ebc-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="70ebc-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="70ebc-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="70ebc-123">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="70ebc-124">Delegáti</span><span class="sxs-lookup"><span data-stu-id="70ebc-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a><span data-ttu-id="70ebc-125">Třídy a objekty</span><span class="sxs-lookup"><span data-stu-id="70ebc-125">Classes and Objects</span></span>  
 <span data-ttu-id="70ebc-126">Podmínky *třída* a *objekt* se někdy používají zcela zaměnitelným významem, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd.</span><span class="sxs-lookup"><span data-stu-id="70ebc-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="70ebc-127">Ano, je volána v rámci vytvoření objektu *vytváření instancí*.</span><span class="sxs-lookup"><span data-stu-id="70ebc-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="70ebc-128">Pomocí analogie plán, podle kterého, třída je plán, podle kterého a v budově z tento plán, podle kterého je objekt.</span><span class="sxs-lookup"><span data-stu-id="70ebc-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="70ebc-129">Chcete-li definovat třídu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="70ebc-130">C# také poskytuje světla verzi třídy názvem *struktury* , jsou užitečné, když potřebujete vytvořit velké pole objektů a proveďte využívat příliš mnoho paměti, pro který chcete.</span><span class="sxs-lookup"><span data-stu-id="70ebc-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="70ebc-131">Chcete-li definovat strukturu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="70ebc-132">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-133">– Třída</span><span class="sxs-lookup"><span data-stu-id="70ebc-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="70ebc-134">Struktura</span><span class="sxs-lookup"><span data-stu-id="70ebc-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a><span data-ttu-id="70ebc-135">Členy třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-135">Class Members</span></span>  
 <span data-ttu-id="70ebc-136">Každá třída může mít různé *třídy členy* , zahrnout vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které zajišťují komunikaci mezi různými třídami a objekty.</span><span class="sxs-lookup"><span data-stu-id="70ebc-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a><span data-ttu-id="70ebc-137">Vlastnosti a pole</span><span class="sxs-lookup"><span data-stu-id="70ebc-137">Properties and Fields</span></span>  
 <span data-ttu-id="70ebc-138">Pole a vlastnosti představují informací, které obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="70ebc-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="70ebc-139">Pole jsou jako proměnné, protože můžou být číst nebo nastavovat přímo.</span><span class="sxs-lookup"><span data-stu-id="70ebc-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="70ebc-140">Chcete-li definovat pole:</span><span class="sxs-lookup"><span data-stu-id="70ebc-140">To define a field:</span></span>  
  
```csharp  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="70ebc-141">Vlastnosti mají get a nastavte postupů, které poskytuje větší kontrolu na tom, jak nastavit nebo vrátil hodnoty.</span><span class="sxs-lookup"><span data-stu-id="70ebc-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="70ebc-142">C# můžete buď vytvořit soukromé pole pro ukládání hodnota vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí, které poskytují základní logiku pro vlastnost postupy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="70ebc-143">Chcete-li definovat ve automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="70ebc-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="70ebc-144">Pokud potřebujete provést některé další operace pro čtení a zápis hodnota vlastnosti definice pole pro ukládání hodnota vlastnosti a poskytují základní logiku pro ukládání a načítání ho:</span><span class="sxs-lookup"><span data-stu-id="70ebc-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="70ebc-145">Většina vlastnosti mají metody nebo postupy, jak nastavit a získat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70ebc-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="70ebc-146">Můžete však vytvořit vlastnosti jen pro čtení, nebo jen pro zápis je omezit změnit nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="70ebc-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="70ebc-147">V jazyce C#, můžete vynechat `get` nebo `set` metoda property.</span><span class="sxs-lookup"><span data-stu-id="70ebc-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="70ebc-148">Automaticky implementované vlastnosti však nemůže být jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="70ebc-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="70ebc-149">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-150">GET</span><span class="sxs-lookup"><span data-stu-id="70ebc-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="70ebc-151">nastavení</span><span class="sxs-lookup"><span data-stu-id="70ebc-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a><span data-ttu-id="70ebc-152">Metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-152">Methods</span></span>  
 <span data-ttu-id="70ebc-153">A *metoda* je akce, která může provádět objekt.</span><span class="sxs-lookup"><span data-stu-id="70ebc-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="70ebc-154">Definovat metodu třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="70ebc-155">Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se budou lišit v počtu parametry nebo typy parametrů.</span><span class="sxs-lookup"><span data-stu-id="70ebc-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="70ebc-156">Chcete-li přetížení metody:</span><span class="sxs-lookup"><span data-stu-id="70ebc-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="70ebc-157">Ve většině případů deklarujte metodu v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="70ebc-158">Však C# také podporuje *rozšiřující metody* které umožňují přidání metody do existující třídy mimo skutečné definice třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="70ebc-159">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-160">Metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="70ebc-161">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="70ebc-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a><span data-ttu-id="70ebc-162">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="70ebc-162">Constructors</span></span>  
 <span data-ttu-id="70ebc-163">Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu.</span><span class="sxs-lookup"><span data-stu-id="70ebc-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="70ebc-164">Konstruktory obvykle inicializovat datových členů nového objektu.</span><span class="sxs-lookup"><span data-stu-id="70ebc-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="70ebc-165">Konstruktor lze spustit pouze po vytvoření třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="70ebc-166">Kromě toho kód v konstruktoru vždy spouští před jakýkoli jiný kód v třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="70ebc-167">Můžete však vytvořit více přetížení konstruktor stejným způsobem jako u jakékoliv jiné metody.</span><span class="sxs-lookup"><span data-stu-id="70ebc-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="70ebc-168">Chcete-li definovat konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="70ebc-169">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-169">For more information, see:</span></span>  
  
 <span data-ttu-id="70ebc-170">[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a><span data-ttu-id="70ebc-171">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-171">Finalizers</span></span>  
 <span data-ttu-id="70ebc-172">Finalizační metody se používají k destruct instance tříd.</span><span class="sxs-lookup"><span data-stu-id="70ebc-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="70ebc-173">V rozhraní .NET Framework bude systém uvolňování automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70ebc-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="70ebc-174">Mohou však stále zapotřebí finalizační metody vyčistit všechny nespravovaných prostředků, které vytváří vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="70ebc-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="70ebc-175">Může existovat pouze jedna finalizační metody pro třídu.</span><span class="sxs-lookup"><span data-stu-id="70ebc-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="70ebc-176">Další informace o finalizační metody a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a><span data-ttu-id="70ebc-177">Události</span><span class="sxs-lookup"><span data-stu-id="70ebc-177">Events</span></span>  
 <span data-ttu-id="70ebc-178">Události povolit třídu nebo objekt, který chcete upozornit ostatní třídy nebo objekty, když něco zájmu dojde.</span><span class="sxs-lookup"><span data-stu-id="70ebc-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="70ebc-179">Třída, která odešle (nebo vyvolá) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *Odběratelé, kteří*.</span><span class="sxs-lookup"><span data-stu-id="70ebc-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="70ebc-180">Další informace o událostech, způsob jejich jsou vyvolány a zpracovávají, najdete v části [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="70ebc-181">Chcete-li deklarovat událost v třídě, použijte [událostí](../../../csharp/language-reference/keywords/event.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="70ebc-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="70ebc-182">Vyvolat událost, vyvolání delegáta události.</span><span class="sxs-lookup"><span data-stu-id="70ebc-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="70ebc-183">K odběru události, použijte `+=` operátor; k odhlášení odběru událostí, použijte `-=` operátor.</span><span class="sxs-lookup"><span data-stu-id="70ebc-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a><span data-ttu-id="70ebc-184">Vnořené třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-184">Nested Classes</span></span>  
 <span data-ttu-id="70ebc-185">Třídy definované v rámci jiné třídy se nazývá *vnořené*.</span><span class="sxs-lookup"><span data-stu-id="70ebc-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="70ebc-186">Ve výchozím nastavení je vnořené třídy soukromé.</span><span class="sxs-lookup"><span data-stu-id="70ebc-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="70ebc-187">K vytvoření instance třídy vnořené, použijte název třídy kontejneru, za nímž následuje tečky a po ní následuje název vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a><span data-ttu-id="70ebc-188">Modifikátory přístupu a úrovně přístupu</span><span class="sxs-lookup"><span data-stu-id="70ebc-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="70ebc-189">Všechny třídy a jejich členové můžete určit, jakou úroveň přístupu poskytují další třídy pomocí *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="70ebc-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="70ebc-190">K dispozici jsou následující modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="70ebc-191">C# – modifikátor</span><span class="sxs-lookup"><span data-stu-id="70ebc-191">C# Modifier</span></span>|<span data-ttu-id="70ebc-192">Definice</span><span class="sxs-lookup"><span data-stu-id="70ebc-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="70ebc-193">veřejné</span><span class="sxs-lookup"><span data-stu-id="70ebc-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="70ebc-194">Typ nebo člen je přístupná jiným kódem ve stejném sestavení nebo jiné sestavení, které na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="70ebc-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="70ebc-195">privátní</span><span class="sxs-lookup"><span data-stu-id="70ebc-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="70ebc-196">Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="70ebc-197">chráněný</span><span class="sxs-lookup"><span data-stu-id="70ebc-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="70ebc-198">Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě nebo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="70ebc-199">interní</span><span class="sxs-lookup"><span data-stu-id="70ebc-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="70ebc-200">Typ nebo člen je přístupný kód ve stejném sestavení, ale nikoli z jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="70ebc-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="70ebc-201">chráněné interní</span><span class="sxs-lookup"><span data-stu-id="70ebc-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="70ebc-202">Typ nebo člen je přístupná žádný kód ve stejném sestavení, nebo všechny odvozené třídy v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="70ebc-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="70ebc-203">privátní chráněný</span><span class="sxs-lookup"><span data-stu-id="70ebc-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="70ebc-204">Typ nebo člen je přístupný kód ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="70ebc-205">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a><span data-ttu-id="70ebc-206">Vytváření instancí třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-206">Instantiating Classes</span></span>  
 <span data-ttu-id="70ebc-207">Pro vytvoření objektu, musíte vytvořit instanci třídy, nebo vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="70ebc-208">Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a vyvolání metody třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="70ebc-209">Chcete-li přiřadit hodnoty k vlastnosti během procesu vytváření instancí třídy, použijte inicializátory objektů:</span><span class="sxs-lookup"><span data-stu-id="70ebc-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="70ebc-210">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-211">New – operátor</span><span class="sxs-lookup"><span data-stu-id="70ebc-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="70ebc-212">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="70ebc-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a><span data-ttu-id="70ebc-213">Statické třídy a členové</span><span class="sxs-lookup"><span data-stu-id="70ebc-213">Static Classes and Members</span></span>  
 <span data-ttu-id="70ebc-214">Statický člen třídy je vlastnost, postup nebo pole, které platí pro všechny instance třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="70ebc-215">Chcete-li definovat je statický člen:</span><span class="sxs-lookup"><span data-stu-id="70ebc-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="70ebc-216">Pro přístup k statický člen, použijte název třídy bez vytvoření objektu této třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="70ebc-217">Statické třídy v jazyce C# mají jenom statické členy a nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="70ebc-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="70ebc-218">Statické členy také přístup k vlastnosti nestatické, pole a metody</span><span class="sxs-lookup"><span data-stu-id="70ebc-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="70ebc-219">Další informace najdete v tématu: [statické](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a><span data-ttu-id="70ebc-220">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-220">Anonymous Types</span></span>  
 <span data-ttu-id="70ebc-221">Anonymní typy umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="70ebc-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="70ebc-222">Kompilátor místo, vygeneruje třídu pro vás.</span><span class="sxs-lookup"><span data-stu-id="70ebc-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="70ebc-223">Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklarace objektu.</span><span class="sxs-lookup"><span data-stu-id="70ebc-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="70ebc-224">Chcete-li vytvořit instanci anonymního typu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="70ebc-225">Další informace najdete v tématu: [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a><span data-ttu-id="70ebc-226">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="70ebc-226">Inheritance</span></span>  
 <span data-ttu-id="70ebc-227">Dědičnost umožňuje vytvořit novou třídu, která opětovně používá rozšiřuje a mění chování, která je definována v jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="70ebc-228">Je volána třídu, jejíž členové jsou děděné *základní třída*, a třídu, která dědí členů, se nazývá *odvozené třídy*.</span><span class="sxs-lookup"><span data-stu-id="70ebc-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="70ebc-229">Ale všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchie tříd rozhraní .NET a poskytuje nižší úroveň služby pro všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ebc-230">C# nepodporuje vícenásobná dědičnost.</span><span class="sxs-lookup"><span data-stu-id="70ebc-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="70ebc-231">To znamená můžete zadat pouze jeden základní třídu pro odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="70ebc-232">Chcete-li zdědit ze základní třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="70ebc-233">Ve výchozím nastavení může být dědí všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-233">By default all classes can be inherited.</span></span> <span data-ttu-id="70ebc-234">Však můžete určit, zda nesmí používat jako základní třída třídy, nebo vytvořte třídu, která lze použít jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="70ebc-235">Chcete-li určit, že třídy nelze použít jako základní třída:</span><span class="sxs-lookup"><span data-stu-id="70ebc-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="70ebc-236">K určení, že třídy lze použít jako základní třída a nelze vytvořit instanci:</span><span class="sxs-lookup"><span data-stu-id="70ebc-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="70ebc-237">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-238">zapečetěná</span><span class="sxs-lookup"><span data-stu-id="70ebc-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="70ebc-239">abstraktní</span><span class="sxs-lookup"><span data-stu-id="70ebc-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a><span data-ttu-id="70ebc-240">Přepis členů</span><span class="sxs-lookup"><span data-stu-id="70ebc-240">Overriding Members</span></span>  
 <span data-ttu-id="70ebc-241">Ve výchozím nastavení odvozené třídy dědí všechny členy ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="70ebc-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="70ebc-242">Pokud chcete změnit chování zděděného členu, budete muset přepsat.</span><span class="sxs-lookup"><span data-stu-id="70ebc-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="70ebc-243">To znamená můžete definovat nové implementace metoda, vlastnost nebo události v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="70ebc-244">Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="70ebc-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="70ebc-245">C# – modifikátor</span><span class="sxs-lookup"><span data-stu-id="70ebc-245">C# Modifier</span></span>|<span data-ttu-id="70ebc-246">Definice</span><span class="sxs-lookup"><span data-stu-id="70ebc-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="70ebc-247">virtuální</span><span class="sxs-lookup"><span data-stu-id="70ebc-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="70ebc-248">Umožňuje člena třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="70ebc-249">přepsání</span><span class="sxs-lookup"><span data-stu-id="70ebc-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="70ebc-250">Přepsání člena virtuální (přepisovatelné) definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="70ebc-251">abstraktní</span><span class="sxs-lookup"><span data-stu-id="70ebc-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="70ebc-252">Vyžaduje, aby člena třídy k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="70ebc-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="70ebc-253">New – modifikátor</span><span class="sxs-lookup"><span data-stu-id="70ebc-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="70ebc-254">Skryje členem zděděn ze základní třídy</span><span class="sxs-lookup"><span data-stu-id="70ebc-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a><span data-ttu-id="70ebc-255">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="70ebc-255">Interfaces</span></span>  
 <span data-ttu-id="70ebc-256">Rozhraní, jako jsou třídy, definovat sadu vlastností, metod a události.</span><span class="sxs-lookup"><span data-stu-id="70ebc-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="70ebc-257">Ale na rozdíl od třídy, rozhraní neposkytují implementace.</span><span class="sxs-lookup"><span data-stu-id="70ebc-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="70ebc-258">Jsou implementované třídy a definován jako samostatné entity z tříd.</span><span class="sxs-lookup"><span data-stu-id="70ebc-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="70ebc-259">Rozhraní představuje kontraktu, v tomto třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.</span><span class="sxs-lookup"><span data-stu-id="70ebc-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="70ebc-260">Definice rozhraní:</span><span class="sxs-lookup"><span data-stu-id="70ebc-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="70ebc-261">K implementaci rozhraní v třídě:</span><span class="sxs-lookup"><span data-stu-id="70ebc-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="70ebc-262">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="70ebc-263">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="70ebc-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="70ebc-264">rozhraní</span><span class="sxs-lookup"><span data-stu-id="70ebc-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a><span data-ttu-id="70ebc-265">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-265">Generics</span></span>  
 <span data-ttu-id="70ebc-266">Třídy, struktury, rozhraní a metody v rozhraní .NET Framework může zahrnovat *parametry typu* , definování typů objektů, které lze uložit nebo použít.</span><span class="sxs-lookup"><span data-stu-id="70ebc-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="70ebc-267">Nejčastější obecných typů je kolekce, kde můžete určit typ objektů, které chcete uložit v kolekci.</span><span class="sxs-lookup"><span data-stu-id="70ebc-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="70ebc-268">Zadat obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-268">To define a generic class:</span></span>  
  
```csharp  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="70ebc-269">Chcete-li vytvořit instanci obecné třídy:</span><span class="sxs-lookup"><span data-stu-id="70ebc-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="70ebc-270">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-271">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="70ebc-272">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="70ebc-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a><span data-ttu-id="70ebc-273">Delegáti</span><span class="sxs-lookup"><span data-stu-id="70ebc-273">Delegates</span></span>  
 <span data-ttu-id="70ebc-274">A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu kompatibilní podpisem.</span><span class="sxs-lookup"><span data-stu-id="70ebc-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="70ebc-275">Můžete vyvolat (nebo volání) metoda prostřednictvím delegáta.</span><span class="sxs-lookup"><span data-stu-id="70ebc-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="70ebc-276">Delegáty se používají pro předávání metod jako argumentů jiným metodám.</span><span class="sxs-lookup"><span data-stu-id="70ebc-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ebc-277">Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="70ebc-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="70ebc-278">Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="70ebc-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="70ebc-279">Pokud chcete vytvořit delegáta:</span><span class="sxs-lookup"><span data-stu-id="70ebc-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="70ebc-280">Pokud chcete vytvořit odkaz na metodu, která odpovídá podpis určeného delegát:</span><span class="sxs-lookup"><span data-stu-id="70ebc-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="70ebc-281">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="70ebc-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="70ebc-282">Delegáti</span><span class="sxs-lookup"><span data-stu-id="70ebc-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="70ebc-283">Delegát</span><span class="sxs-lookup"><span data-stu-id="70ebc-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="70ebc-284">Viz také</span><span class="sxs-lookup"><span data-stu-id="70ebc-284">See Also</span></span>  
 [<span data-ttu-id="70ebc-285">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="70ebc-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
