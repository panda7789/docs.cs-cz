---
title: "class (Referenční dokumentace jazyka C#)"
ms.date: 07/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae4b019ee88b6f331a76c750ab94fc76a3343adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="class-c-reference"></a><span data-ttu-id="c9854-102">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c9854-102">class (C# Reference)</span></span>

<span data-ttu-id="c9854-103">Třídy jsou deklarovány pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c9854-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates 
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="c9854-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9854-104">Remarks</span></span>
<span data-ttu-id="c9854-105">V jazyce C# je povolena pouze jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="c9854-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="c9854-106">Třída jinými slovy, můžete implementace dědí pouze jeden základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c9854-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="c9854-107">Třída, však může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9854-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="c9854-108">V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c9854-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="c9854-109">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="c9854-109">Inheritance</span></span>|<span data-ttu-id="c9854-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9854-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="c9854-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9854-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="c9854-112">Single</span><span class="sxs-lookup"><span data-stu-id="c9854-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="c9854-113">NONE, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9854-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="c9854-114">Jedinou implementuje jedno rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9854-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="c9854-115">Třídy, které je deklarovat přímo v rámci oboru názvů, nejsou vnořené v rámci jiné třídy, může být buď [veřejné](../../../csharp/language-reference/keywords/public.md) nebo [interní](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="c9854-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="c9854-116">Třídy jsou `internal` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c9854-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="c9854-117">Členy třídy, včetně vnořené třídy, může být [veřejné](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [privátní](../../../csharp/language-reference/keywords/private.md), nebo `private protected`.</span><span class="sxs-lookup"><span data-stu-id="c9854-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [private](../../../csharp/language-reference/keywords/private.md), or `private protected`.</span></span> <span data-ttu-id="c9854-118">Členy jsou [privátní](../../../csharp/language-reference/keywords/private.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c9854-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="c9854-119">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c9854-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="c9854-120">Obecné třídy, které mají parametry typu můžou deklarovat.</span><span class="sxs-lookup"><span data-stu-id="c9854-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="c9854-121">Další informace najdete v tématu [obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c9854-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="c9854-122">Třída může obsahovat deklarace následující členy:</span><span class="sxs-lookup"><span data-stu-id="c9854-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="c9854-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c9854-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="c9854-124">Konstanty</span><span class="sxs-lookup"><span data-stu-id="c9854-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="c9854-125">Pole</span><span class="sxs-lookup"><span data-stu-id="c9854-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="c9854-126">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="c9854-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="c9854-127">Metody</span><span class="sxs-lookup"><span data-stu-id="c9854-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="c9854-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c9854-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="c9854-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="c9854-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="c9854-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="c9854-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="c9854-131">Události</span><span class="sxs-lookup"><span data-stu-id="c9854-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="c9854-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="c9854-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="c9854-133">Třídy</span><span class="sxs-lookup"><span data-stu-id="c9854-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="c9854-134">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9854-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="c9854-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="c9854-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a><span data-ttu-id="c9854-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9854-136">Example</span></span>
<span data-ttu-id="c9854-137">Následující příklad ukazuje deklarující třída polí, konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="c9854-137">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="c9854-138">Také ukazuje vytvoření instance objektu a tisk data instance.</span><span class="sxs-lookup"><span data-stu-id="c9854-138">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="c9854-139">V tomto příkladu jsou deklarovány dvou tříd.</span><span class="sxs-lookup"><span data-stu-id="c9854-139">In this example, two classes are declared.</span></span> <span data-ttu-id="c9854-140">První třída `Child`, obsahuje dva privátní polí (`name` a `age`), dvě veřejné konstruktory a jedna veřejná metoda.</span><span class="sxs-lookup"><span data-stu-id="c9854-140">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="c9854-141">Druhé třídy `StringTest`, se používá pro jiné `Main`.</span><span class="sxs-lookup"><span data-stu-id="c9854-141">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]

## <a name="comments"></a><span data-ttu-id="c9854-142">Komentáře</span><span class="sxs-lookup"><span data-stu-id="c9854-142">Comments</span></span>
<span data-ttu-id="c9854-143">Všimněte si, že se v předchozím příkladu privátním polím (`name` a `age`) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy.</span><span class="sxs-lookup"><span data-stu-id="c9854-143">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="c9854-144">Její název, například nelze tisknout z `Main` metodu, pomocí příkazu takto:</span><span class="sxs-lookup"><span data-stu-id="c9854-144">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="c9854-145">Přístup ke členům privátní `Child` z `Main` pouze by bylo možné Pokud `Main` byly člena třídy.</span><span class="sxs-lookup"><span data-stu-id="c9854-145">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="c9854-146">Typy deklarovat uvnitř třídu bez výchozí modifikátor přístupu k `private`, takže stále datových členů v tomto příkladu by `private` Pokud klíčové slovo byly odebrány.</span><span class="sxs-lookup"><span data-stu-id="c9854-146">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="c9854-147">Nakonec, Všimněte si, že pro objekt vytvořený pomocí výchozího konstruktoru (`child3`), pole byla inicializována tak, aby stáří nula ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c9854-147">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c9854-148">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c9854-148">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c9854-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9854-149">See Also</span></span>
 [<span data-ttu-id="c9854-150">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c9854-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c9854-151">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c9854-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c9854-152">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c9854-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c9854-153">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="c9854-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
