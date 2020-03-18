---
title: Třídy - Průvodce programováním jazyka C#
description: Informace o typech tříd a jejich vytváření
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: aadf555fb47963eab323bbb6105227c5b119e6f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170309"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="fae80-103">Třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fae80-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="fae80-104">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="fae80-104">Reference types</span></span>  
<span data-ttu-id="fae80-105">Typ, který je definován jako [třída,](../../language-reference/keywords/class.md) je *typ odkazu*.</span><span class="sxs-lookup"><span data-stu-id="fae80-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="fae80-106">Za běhu, když deklarujete proměnnou typu odkazu, proměnná obsahuje hodnotu [null,](../../language-reference/keywords/null.md) dokud explicitně nevytvoříte instanci třídy pomocí [nového](../../language-reference/operators/new-operator.md) operátoru, nebo jí přiřadíte objekt kompatibilního typu, který mohl být vytvořen jinde, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fae80-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="fae80-107">Při vytvoření objektu je na spravované haldě pro daný objekt přidělendostatek paměti a proměnná obsahuje pouze odkaz na umístění uvedeného objektu.</span><span class="sxs-lookup"><span data-stu-id="fae80-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="fae80-108">Typy na spravované haldy vyžadují režii, jak při přidělení, tak při jejich uvolnění funkcí automatické správy paměti CLR, která je známá jako *uvolňování paměti*.</span><span class="sxs-lookup"><span data-stu-id="fae80-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="fae80-109">Uvolňování paměti je však také vysoce optimalizované a ve většině scénářů nevytváří problém s výkonem.</span><span class="sxs-lookup"><span data-stu-id="fae80-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="fae80-110">Další informace o uvolňování paměti naleznete v [tématu Automatická správa paměti a uvolňování paměti](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="fae80-111">Deklarace tříd</span><span class="sxs-lookup"><span data-stu-id="fae80-111">Declaring Classes</span></span>

 <span data-ttu-id="fae80-112">Třídy jsou deklarovány pomocí klíčového slova [třídy](../../language-reference/keywords/class.md) následovaného jedinečným identifikátorem, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="fae80-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="fae80-113">Klíčovému `class` slovu předchází úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="fae80-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="fae80-114">Vzhledem k tomu, [že veřejné](../../language-reference/keywords/public.md) se používá v tomto případě, kdokoli můžete vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="fae80-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="fae80-115">Název třídy následuje za `class` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="fae80-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="fae80-116">Název třídy musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)Jazyka C# .</span><span class="sxs-lookup"><span data-stu-id="fae80-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="fae80-117">Zbývající část definice je tělo třídy, kde jsou definovány chování a data.</span><span class="sxs-lookup"><span data-stu-id="fae80-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="fae80-118">Pole, vlastnosti, metody a události ve třídě jsou souhrnně označovány jako *členové třídy*.</span><span class="sxs-lookup"><span data-stu-id="fae80-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="fae80-119">Vytváření objektů</span><span class="sxs-lookup"><span data-stu-id="fae80-119">Creating objects</span></span>

<span data-ttu-id="fae80-120">I když jsou někdy používány zaměnitelně, třída a objekt jsou různé věci.</span><span class="sxs-lookup"><span data-stu-id="fae80-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="fae80-121">Třída definuje typ objektu, ale není samotnýobjekt.</span><span class="sxs-lookup"><span data-stu-id="fae80-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="fae80-122">Objekt je konkrétní entita založená na třídě a je někdy označována jako instance třídy.</span><span class="sxs-lookup"><span data-stu-id="fae80-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="fae80-123">Objekty lze vytvořit pomocí [novéklíčové](../../language-reference/operators/new-operator.md) slovo následuje název třídy, která bude založena na objektu, například takto:</span><span class="sxs-lookup"><span data-stu-id="fae80-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="fae80-124">Při vytvoření instance třídy je odkaz na objekt předán zpět programátorovi.</span><span class="sxs-lookup"><span data-stu-id="fae80-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="fae80-125">V předchozím příkladu je odkaz na `object1` objekt, `Customer`který je založen na .</span><span class="sxs-lookup"><span data-stu-id="fae80-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="fae80-126">Tento odkaz odkazuje na nový objekt, ale neobsahuje samotná data objektu.</span><span class="sxs-lookup"><span data-stu-id="fae80-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="fae80-127">Ve skutečnosti můžete vytvořit odkaz na objekt bez vytvoření objektu vůbec:</span><span class="sxs-lookup"><span data-stu-id="fae80-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="fae80-128">Nedoporučujeme vytvářet odkazy na objekty, jako je tento, které neodkazují na objekt, protože pokus o přístup k objektu prostřednictvím takového odkazu se nezdaří za běhu.</span><span class="sxs-lookup"><span data-stu-id="fae80-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="fae80-129">Takový odkaz však lze odkazovat na objekt, buď vytvořením nového objektu, nebo jeho přiřazením k existujícímu objektu, například takto:</span><span class="sxs-lookup"><span data-stu-id="fae80-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="fae80-130">Tento kód vytvoří dva odkazy na objekty, které oba odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="fae80-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="fae80-131">Proto všechny změny objektu `object3` provedené prostřednictvím se `object4`projeví v následné použití .</span><span class="sxs-lookup"><span data-stu-id="fae80-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="fae80-132">Vzhledem k tomu, že objekty, které jsou založeny na třídách, jsou označovány odkazem, jsou třídy označovány jako typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="fae80-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="fae80-133">Dědičnost třídy</span><span class="sxs-lookup"><span data-stu-id="fae80-133">Class inheritance</span></span>  

<span data-ttu-id="fae80-134">Třídy plně podporují *dědičnost*, základní charakteristiku objektově orientovaného programování.</span><span class="sxs-lookup"><span data-stu-id="fae80-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="fae80-135">Při vytváření třídy můžete dědit z jakéhokoli jiného rozhraní nebo třídy, která není definována jako [zapečetěné](../../language-reference/keywords/sealed.md)a jiné třídy mohou dědit z vaší třídy a přepsat třídy virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="fae80-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="fae80-136">Dědičnost se provádí pomocí *odvození*, což znamená, že třída je deklarována pomocí *základní třídy,* ze které dědí data a chování.</span><span class="sxs-lookup"><span data-stu-id="fae80-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="fae80-137">Základní třída je určena připojením dvojtečky a názvu základní třídy za názvem odvozené třídy, například takto:</span><span class="sxs-lookup"><span data-stu-id="fae80-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="fae80-138">Když třída deklaruje základní třídu, dědí všechny členy základní třídy s výjimkou konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="fae80-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="fae80-139">Další informace naleznete v [tématu Dědičnost](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="fae80-140">Na rozdíl od Jazyka C++ může třída v jazyce C# přímo dědit pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fae80-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="fae80-141">Však vzhledem k tomu, že základní třída může dědit z jiné třídy, třída může nepřímo dědit více základních tříd.</span><span class="sxs-lookup"><span data-stu-id="fae80-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="fae80-142">Kromě toho třídy můžete přímo implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fae80-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="fae80-143">Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="fae80-144">Třída může být deklarována [jako abstraktní](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="fae80-145">Abstraktní třída obsahuje abstraktní metody, které mají definici podpisu, ale žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="fae80-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="fae80-146">Abstraktní třídy nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="fae80-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="fae80-147">Lze je použít pouze prostřednictvím odvozených tříd, které implementují abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="fae80-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="fae80-148">Naproti tomu [zapečetěné](../../language-reference/keywords/sealed.md) třídy neumožňuje jiné třídy odvodit z něj.</span><span class="sxs-lookup"><span data-stu-id="fae80-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="fae80-149">Další informace naleznete [v tématu Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="fae80-150">Definice tříd lze rozdělit mezi různé zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="fae80-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="fae80-151">Další informace naleznete [v tématu Částečné třídy a metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="fae80-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fae80-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="fae80-152">Example</span></span>

<span data-ttu-id="fae80-153">Následující příklad definuje veřejnou třídu, která obsahuje [automaticky implementovanou vlastnost](auto-implemented-properties.md), metodu a speciální metodu nazvanou konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fae80-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="fae80-154">Další informace naleznete v [tématech Vlastnosti](properties.md), [Metody](methods.md)a [Konstruktory](constructors.md) témata.</span><span class="sxs-lookup"><span data-stu-id="fae80-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="fae80-155">Instance třídy jsou pak vytvořena instance s `new` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="fae80-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="fae80-156">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fae80-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fae80-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="fae80-157">See also</span></span>

- [<span data-ttu-id="fae80-158">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fae80-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fae80-159">Objektově orientované programování</span><span class="sxs-lookup"><span data-stu-id="fae80-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="fae80-160">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="fae80-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="fae80-161">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="fae80-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="fae80-162">Členové</span><span class="sxs-lookup"><span data-stu-id="fae80-162">Members</span></span>](members.md)
- [<span data-ttu-id="fae80-163">Metody</span><span class="sxs-lookup"><span data-stu-id="fae80-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="fae80-164">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="fae80-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="fae80-165">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="fae80-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="fae80-166">Objekty</span><span class="sxs-lookup"><span data-stu-id="fae80-166">Objects</span></span>](objects.md)
