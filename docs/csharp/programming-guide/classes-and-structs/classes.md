---
title: Třídy – C# Průvodce programováním
ms.custom: seodec18
description: Seznamte se s typy třídy a jak je vytvořit
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: ad19099242a3bedbb7283219dfd7733db13231ec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398594"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="0415a-103">Třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0415a-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="0415a-104">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="0415a-104">Reference types</span></span>  
<span data-ttu-id="0415a-105">Typ, který je definován jako [třídy](../../../csharp/language-reference/keywords/class.md) je *odkazovat na typ*.</span><span class="sxs-lookup"><span data-stu-id="0415a-105">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="0415a-106">V době běhu při deklarování proměnné typu odkazu proměnná obsahuje hodnotu [null](../../../csharp/language-reference/keywords/null.md) dokud explicitně nevytvoříte instanci třídy pomocí [nové](../../../csharp/language-reference/operators/new-operator.md) operátor nebo jí nepřiřadíte objekt kompatibilní typ, který byl možná vytvořen jinde, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0415a-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="0415a-107">Při vytvoření objektu je dostatečná paměť je přidělena na spravované haldě pro tento konkrétní objekt a proměnná obsahuje pouze odkaz na umístění uvedené objektu.</span><span class="sxs-lookup"><span data-stu-id="0415a-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="0415a-108">Typy na spravované haldě zdržovat při přidělování i při jejich převzetí pomocí funkce správy automatické paměti modulu CLR, která se nazývá *uvolňování*.</span><span class="sxs-lookup"><span data-stu-id="0415a-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="0415a-109">Nicméně uvolňování paměti je také vysoce optimalizováno a ve většině případů nedojde k vytvoření problému s výkonem.</span><span class="sxs-lookup"><span data-stu-id="0415a-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="0415a-110">Další informace o uvolňování paměti naleznete v tématu [paměti automatické správy a uvolňování paměti kolekce](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="0415a-111">Deklarace tříd</span><span class="sxs-lookup"><span data-stu-id="0415a-111">Declaring Classes</span></span>

 <span data-ttu-id="0415a-112">Třídy jsou deklarované pomocí [třídy](../../../csharp/language-reference/keywords/class.md) – klíčové slovo, za nímž následuje jedinečný identifikátor, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0415a-112">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="0415a-113">`class` – Klíčové slovo předchází úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="0415a-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="0415a-114">Protože [veřejné](../../language-reference/keywords/public.md) se používá v tomto případě Kdokoliv může vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="0415a-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="0415a-115">Následuje název třídy `class` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0415a-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="0415a-116">Název třídy musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="0415a-117">Zbývající část definice je tělo třídy, kde jsou definovány chování a data.</span><span class="sxs-lookup"><span data-stu-id="0415a-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="0415a-118">Pole, vlastnosti, metody a události na třídu se souhrnně označují jako *členy třídy*.</span><span class="sxs-lookup"><span data-stu-id="0415a-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="0415a-119">Vytváření objektů</span><span class="sxs-lookup"><span data-stu-id="0415a-119">Creating objects</span></span>

<span data-ttu-id="0415a-120">Přestože se někdy používají Zaměnitelně, třídy a objekt jsou různé věci.</span><span class="sxs-lookup"><span data-stu-id="0415a-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="0415a-121">Třída definuje typ objektu, ale není samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="0415a-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="0415a-122">Objekt je konkrétní entity podle třídy a jsou někdy označovány jako instance třídy.</span><span class="sxs-lookup"><span data-stu-id="0415a-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="0415a-123">Objekty mohou být vytvořeny pomocí [nové](../../language-reference/operators/new-operator.md) – klíčové slovo, za nímž následuje název třídy, která objekt bude založen na, tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="0415a-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="0415a-124">Když je vytvořena instance třídy, odkaz na objekt je předán zpět na programátorovi.</span><span class="sxs-lookup"><span data-stu-id="0415a-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="0415a-125">V předchozím příkladu `object1` je odkaz na objekt, který je založen na `Customer`.</span><span class="sxs-lookup"><span data-stu-id="0415a-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="0415a-126">Tento odkaz odkazuje na nový objekt, ale neobsahuje vlastní data objektu.</span><span class="sxs-lookup"><span data-stu-id="0415a-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="0415a-127">Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření všech objektů:</span><span class="sxs-lookup"><span data-stu-id="0415a-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="0415a-128">Nedoporučujeme ale, vytváření odkazů na objekty, jako je například tento, které není odkaz na objekt, protože se pokouší získat přístup k objektu prostřednictvím odkazu selže v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0415a-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="0415a-129">Však můžete provést odkazu k odkazování na objekt, buď tak, že vytvoříte nový objekt, nebo jejím přiřazením k existující objekt, jako je například tento:</span><span class="sxs-lookup"><span data-stu-id="0415a-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="0415a-130">Tento kód vytvoří dva odkazy na objekty, které odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="0415a-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="0415a-131">Proto všechny změny provedené prostřednictvím objektu `object3` se projeví v následné použití `object4`.</span><span class="sxs-lookup"><span data-stu-id="0415a-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="0415a-132">Protože objekty, které jsou založeny na třídách jsou uvedené odkazem, třídy jsou označovány jako referenční typy.</span><span class="sxs-lookup"><span data-stu-id="0415a-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="0415a-133">Dědičnost tříd</span><span class="sxs-lookup"><span data-stu-id="0415a-133">Class inheritance</span></span>  

<span data-ttu-id="0415a-134">Třídy plně podporují *dědičnosti*, základní charakteristiku objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="0415a-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="0415a-135">Při vytváření třídy můžete dědit ze kteréhokoli rozhraní nebo třídu, která není definován jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat třídy virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="0415a-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="0415a-136">Dědičnost se dá udělat pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třída* ze které dědí data a chování.</span><span class="sxs-lookup"><span data-stu-id="0415a-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="0415a-137">Základní třída zadaná přidáním dvojtečku a název základní třídy za název odvozené třídy takto:</span><span class="sxs-lookup"><span data-stu-id="0415a-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="0415a-138">Třída deklaruje základní třídu, zdědí všechny členy základní třídy s výjimkou konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="0415a-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="0415a-139">Další informace najdete v tématu [dědičnosti](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="0415a-140">Na rozdíl od C++ třídy v jazyce C# může dědit pouze přímo z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0415a-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="0415a-141">Ale protože samotný základní třída může dědit z jiné třídy, třída může nepřímo dědit více základních tříd.</span><span class="sxs-lookup"><span data-stu-id="0415a-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="0415a-142">Třída navíc můžete přímo implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0415a-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="0415a-143">Další informace najdete v tématu [rozhraní](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="0415a-144">Třídy lze deklarovat [abstraktní](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="0415a-145">Abstraktní třída obsahuje abstraktní metody, které mají definici podpis ale nemá žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="0415a-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="0415a-146">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="0415a-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="0415a-147">Je možné použít pouze prostřednictvím odvozené třídy, které implementují abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="0415a-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="0415a-148">Naopak [zapečetěné](../../language-reference/keywords/sealed.md) třídy nepovoluje ostatní třídy odvozovat z něj.</span><span class="sxs-lookup"><span data-stu-id="0415a-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="0415a-149">Další informace najdete v tématu [abstraktní a zapečetěné třídy a členové](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="0415a-150">Definice tříd lze rozdělit do jiných zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="0415a-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="0415a-151">Další informace najdete v tématu [částečné třídy a metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0415a-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0415a-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="0415a-152">Example</span></span>

<span data-ttu-id="0415a-153">Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementované vlastnosti](auto-implemented-properties.md), metoda a speciální metoda volá konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0415a-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="0415a-154">Další informace najdete v tématu [vlastnosti](properties.md), [metody](methods.md), a [konstruktory](constructors.md) témata.</span><span class="sxs-lookup"><span data-stu-id="0415a-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="0415a-155">Instance třídy jsou pak vytvořeny s `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0415a-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="0415a-156">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0415a-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0415a-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0415a-157">See also</span></span>

- [<span data-ttu-id="0415a-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0415a-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0415a-159">Objektově orientované programování</span><span class="sxs-lookup"><span data-stu-id="0415a-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="0415a-160">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="0415a-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="0415a-161">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="0415a-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="0415a-162">Členové</span><span class="sxs-lookup"><span data-stu-id="0415a-162">Members</span></span>](members.md)
- [<span data-ttu-id="0415a-163">Metody</span><span class="sxs-lookup"><span data-stu-id="0415a-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="0415a-164">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="0415a-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="0415a-165">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="0415a-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="0415a-166">Objekty</span><span class="sxs-lookup"><span data-stu-id="0415a-166">Objects</span></span>](objects.md)
