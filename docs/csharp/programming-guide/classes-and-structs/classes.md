---
title: Třídy – C# Průvodce programováním
description: Přečtěte si o typech tříd a o tom, jak je vytvořit
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 832095e1d9712c85ad588836e8eba8f523719021
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714978"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="d49bd-103">Třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d49bd-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="d49bd-104">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="d49bd-104">Reference types</span></span>  
<span data-ttu-id="d49bd-105">Typ, který je definován jako [Třída](../../language-reference/keywords/class.md) , je *odkazový typ*.</span><span class="sxs-lookup"><span data-stu-id="d49bd-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="d49bd-106">V době běhu, pokud deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null](../../language-reference/keywords/null.md) , dokud explicitně nevytvoříte instanci třídy pomocí operátoru [New](../../language-reference/operators/new-operator.md) , nebo přiřadíte objekt kompatibilního typu, který mohl být vytvořen jinde, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d49bd-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="d49bd-107">Když je objekt vytvořen, je k dispozici dostatek paměti na spravované haldě pro daný objekt a proměnná obsahuje pouze odkaz na umístění daného objektu.</span><span class="sxs-lookup"><span data-stu-id="d49bd-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="d49bd-108">Typy na spravované haldě vyžadují režii při jejich přidělování a v případě, že jsou uvolněny automatickou funkcí správy paměti modulu CLR, která se označuje jako *uvolňování*paměti.</span><span class="sxs-lookup"><span data-stu-id="d49bd-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="d49bd-109">Uvolňování paměti je ale také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem.</span><span class="sxs-lookup"><span data-stu-id="d49bd-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="d49bd-110">Další informace o uvolňování paměti najdete v tématu [Automatická správa paměti a uvolňování](../../../standard/garbage-collection/gc.md)paměti.</span><span class="sxs-lookup"><span data-stu-id="d49bd-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="d49bd-111">Deklarace tříd</span><span class="sxs-lookup"><span data-stu-id="d49bd-111">Declaring Classes</span></span>

 <span data-ttu-id="d49bd-112">Třídy jsou deklarovány pomocí klíčového slova [Class](../../language-reference/keywords/class.md) následovaný jedinečným identifikátorem, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d49bd-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="d49bd-113">Klíčovému slovu `class` předchází úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="d49bd-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="d49bd-114">Vzhledem k tomu, že v tomto případě je použita možnost [Public](../../language-reference/keywords/public.md) , může kdokoli vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="d49bd-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="d49bd-115">Název třídy následuje klíčové slovo `class`.</span><span class="sxs-lookup"><span data-stu-id="d49bd-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="d49bd-116">Název třídy musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="d49bd-117">Zbytek definice je tělo třídy, kde jsou definovány chování a data.</span><span class="sxs-lookup"><span data-stu-id="d49bd-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="d49bd-118">Pole, vlastnosti, metody a události třídy jsou souhrnně označovány jako *členy třídy*.</span><span class="sxs-lookup"><span data-stu-id="d49bd-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="d49bd-119">Vytváření objektů</span><span class="sxs-lookup"><span data-stu-id="d49bd-119">Creating objects</span></span>

<span data-ttu-id="d49bd-120">I když se někdy používají jako zaměnitelné, třída a objekt jsou různé věci.</span><span class="sxs-lookup"><span data-stu-id="d49bd-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="d49bd-121">Třída definuje typ objektu, ale není to samotný objekt.</span><span class="sxs-lookup"><span data-stu-id="d49bd-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="d49bd-122">Objekt je konkrétní entita založená na třídě a je někdy označována jako instance třídy.</span><span class="sxs-lookup"><span data-stu-id="d49bd-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="d49bd-123">Objekty lze vytvořit pomocí klíčového slova [New](../../language-reference/operators/new-operator.md) následovaného názvem třídy, na které bude objekt založen, podobně jako toto:</span><span class="sxs-lookup"><span data-stu-id="d49bd-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="d49bd-124">Když je vytvořena instance třídy, odkaz na objekt je předán zpět do programátora.</span><span class="sxs-lookup"><span data-stu-id="d49bd-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="d49bd-125">V předchozím příkladu je `object1` odkazem na objekt, který je založen na `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d49bd-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="d49bd-126">Tento odkaz odkazuje na nový objekt, ale neobsahuje data objektu samotné.</span><span class="sxs-lookup"><span data-stu-id="d49bd-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="d49bd-127">Ve skutečnosti můžete vytvořit odkaz na objekt, aniž byste vůbec vytvořili objekt:</span><span class="sxs-lookup"><span data-stu-id="d49bd-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="d49bd-128">Nedoporučujeme vytvářet odkazy na objekty, jako je takový, který neodkazuje na objekt, protože při pokusu o přístup k objektu prostřednictvím takového odkazu se v době běhu nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d49bd-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="d49bd-129">Takový odkaz však lze použít pro odkazování na objekt, buď vytvořením nového objektu, nebo přiřazením k existujícímu objektu, například:</span><span class="sxs-lookup"><span data-stu-id="d49bd-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="d49bd-130">Tento kód vytvoří dva odkazy na objekty, které odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="d49bd-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="d49bd-131">Proto se všechny změny objektu provedené pomocí `object3` projeví v následných použitích `object4`.</span><span class="sxs-lookup"><span data-stu-id="d49bd-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="d49bd-132">Vzhledem k tomu, že objekty, které jsou založeny na třídách, jsou odkazovány odkazem, třídy jsou označovány jako typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="d49bd-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="d49bd-133">Dědičnost tříd</span><span class="sxs-lookup"><span data-stu-id="d49bd-133">Class inheritance</span></span>  

<span data-ttu-id="d49bd-134">Třídy plně podporují *Dědičnost*, základní charakteristiky objektově orientovaného programování.</span><span class="sxs-lookup"><span data-stu-id="d49bd-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="d49bd-135">Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [sealed](../../language-reference/keywords/sealed.md), a jiné třídy mohou dědit z vaší třídy a přepsat virtuální metody třídy.</span><span class="sxs-lookup"><span data-stu-id="d49bd-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="d49bd-136">Dědičnost je provedeno pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třídy* , ze které dědí data a chování.</span><span class="sxs-lookup"><span data-stu-id="d49bd-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="d49bd-137">Základní třída je určena připojením dvojtečky a názvem základní třídy za názvem odvozené třídy, například takto:</span><span class="sxs-lookup"><span data-stu-id="d49bd-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="d49bd-138">Když třída deklaruje základní třídu, dědí všechny členy základní třídy s výjimkou konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d49bd-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="d49bd-139">Další informace najdete v tématu [Dědičnost](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="d49bd-140">Na rozdíl C++od, třída v C# může přímo dědit pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="d49bd-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="d49bd-141">Protože však základní třída může dědit z jiné třídy, třída může nepřímo zdědit více základních tříd.</span><span class="sxs-lookup"><span data-stu-id="d49bd-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="d49bd-142">Kromě toho třída může přímo implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d49bd-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="d49bd-143">Další informace naleznete v tématu [rozhraní](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="d49bd-144">Třída může být deklarována jako [abstraktní](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="d49bd-145">Abstraktní třída obsahuje abstraktní metody, které mají definici signatury, ale žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="d49bd-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="d49bd-146">Nelze vytvořit instanci abstraktních tříd.</span><span class="sxs-lookup"><span data-stu-id="d49bd-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="d49bd-147">Lze je použít pouze prostřednictvím odvozených tříd, které implementují abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="d49bd-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="d49bd-148">Naproti tomu [zapečetěná](../../language-reference/keywords/sealed.md) třída nepovoluje odvození jiných tříd.</span><span class="sxs-lookup"><span data-stu-id="d49bd-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="d49bd-149">Další informace naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="d49bd-150">Definice tříd mohou být rozděleny mezi různé zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="d49bd-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="d49bd-151">Další informace naleznete v tématu [částečné třídy a metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d49bd-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d49bd-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="d49bd-152">Example</span></span>

<span data-ttu-id="d49bd-153">Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementovanou vlastnost](auto-implemented-properties.md), metodu a speciální metodu, která se nazývá konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d49bd-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="d49bd-154">Další informace naleznete v tématech [vlastnosti](properties.md), [metody](methods.md)a [konstruktory](constructors.md) .</span><span class="sxs-lookup"><span data-stu-id="d49bd-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="d49bd-155">Instance třídy se pak vytvoří s klíčovým slovem `new`.</span><span class="sxs-lookup"><span data-stu-id="d49bd-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="d49bd-156">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="d49bd-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d49bd-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d49bd-157">See also</span></span>

- [<span data-ttu-id="d49bd-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d49bd-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d49bd-159">Objektově orientované programování</span><span class="sxs-lookup"><span data-stu-id="d49bd-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="d49bd-160">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="d49bd-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="d49bd-161">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="d49bd-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="d49bd-162">Členové</span><span class="sxs-lookup"><span data-stu-id="d49bd-162">Members</span></span>](members.md)
- [<span data-ttu-id="d49bd-163">Metody</span><span class="sxs-lookup"><span data-stu-id="d49bd-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="d49bd-164">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d49bd-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="d49bd-165">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="d49bd-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="d49bd-166">Objekty</span><span class="sxs-lookup"><span data-stu-id="d49bd-166">Objects</span></span>](objects.md)
