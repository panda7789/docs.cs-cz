---
title: Class – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: ea1e2e049a692fb9d86731c8a450b568f275f9a9
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924795"
---
# <a name="class-c-reference"></a><span data-ttu-id="f6c88-102">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f6c88-102">class (C# Reference)</span></span>

<span data-ttu-id="f6c88-103">Třídy jsou deklarované pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f6c88-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="f6c88-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6c88-104">Remarks</span></span>

<span data-ttu-id="f6c88-105">V jazyce C# je povolena pouze jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="f6c88-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="f6c88-106">Jinými slovy třída může dědit implementace z pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="f6c88-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="f6c88-107">Nicméně třída může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f6c88-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="f6c88-108">Následující tabulka uvádí příklady dědičnost třídy a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="f6c88-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="f6c88-109">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="f6c88-109">Inheritance</span></span>|<span data-ttu-id="f6c88-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6c88-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="f6c88-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6c88-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="f6c88-112">Single</span><span class="sxs-lookup"><span data-stu-id="f6c88-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="f6c88-113">NONE, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6c88-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="f6c88-114">Jediné, jedno rozhraní implementuje</span><span class="sxs-lookup"><span data-stu-id="f6c88-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="f6c88-115">Třídy, které deklarujete přímo v rámci oboru názvů, ne vnořené v rámci jiné třídy, může být buď [veřejné](../../../csharp/language-reference/keywords/public.md) nebo [interní](../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="f6c88-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](../../../csharp/language-reference/keywords/public.md) or [internal](../../../csharp/language-reference/keywords/internal.md).</span></span> <span data-ttu-id="f6c88-116">Třídy jsou `internal` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f6c88-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="f6c88-117">Členy třídy, včetně vnořené třídy, může být [veřejné](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [privátní](../../../csharp/language-reference/keywords/private.md), nebo `private protected`.</span><span class="sxs-lookup"><span data-stu-id="f6c88-117">Class members, including nested classes, can be [public](../../../csharp/language-reference/keywords/public.md), `protected internal`, [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [private](../../../csharp/language-reference/keywords/private.md), or `private protected`.</span></span> <span data-ttu-id="f6c88-118">Jsou členové [privátní](../../../csharp/language-reference/keywords/private.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f6c88-118">Members are [private](../../../csharp/language-reference/keywords/private.md) by default.</span></span>

<span data-ttu-id="f6c88-119">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f6c88-119">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="f6c88-120">Je možné deklarovat obecných tříd, které má parametry typu.</span><span class="sxs-lookup"><span data-stu-id="f6c88-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="f6c88-121">Další informace najdete v tématu [obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="f6c88-121">For more information, see [Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="f6c88-122">Třída může obsahovat deklarace následující členy:</span><span class="sxs-lookup"><span data-stu-id="f6c88-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="f6c88-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="f6c88-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="f6c88-124">Konstanty</span><span class="sxs-lookup"><span data-stu-id="f6c88-124">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="f6c88-125">Pole</span><span class="sxs-lookup"><span data-stu-id="f6c88-125">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="f6c88-126">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="f6c88-126">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="f6c88-127">Metody</span><span class="sxs-lookup"><span data-stu-id="f6c88-127">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="f6c88-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f6c88-128">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="f6c88-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="f6c88-129">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)

- [<span data-ttu-id="f6c88-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="f6c88-130">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="f6c88-131">Události</span><span class="sxs-lookup"><span data-stu-id="f6c88-131">Events</span></span>](../../../csharp/programming-guide/events/index.md)

- [<span data-ttu-id="f6c88-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="f6c88-132">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="f6c88-133">Třídy</span><span class="sxs-lookup"><span data-stu-id="f6c88-133">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="f6c88-134">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6c88-134">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

- [<span data-ttu-id="f6c88-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="f6c88-135">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="f6c88-136">Výčty</span><span class="sxs-lookup"><span data-stu-id="f6c88-136">Enumerations</span></span>](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="f6c88-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6c88-137">Example</span></span>

<span data-ttu-id="f6c88-138">Následující příklad ukazuje deklarující polí tříd, konstruktory a metody.</span><span class="sxs-lookup"><span data-stu-id="f6c88-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="f6c88-139">Také ukazuje vytvoření instance objektu a tisk data instance.</span><span class="sxs-lookup"><span data-stu-id="f6c88-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="f6c88-140">V tomto příkladu dvě třídy jsou deklarované.</span><span class="sxs-lookup"><span data-stu-id="f6c88-140">In this example, two classes are declared.</span></span> <span data-ttu-id="f6c88-141">První třída `Child`, obsahuje dvě soukromé pole (`name` a `age`), dvě veřejné konstruktory a jednu veřejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="f6c88-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="f6c88-142">Druhá třída `StringTest`, se používá pro jiné `Main`.</span><span class="sxs-lookup"><span data-stu-id="f6c88-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="f6c88-143">Komentáře</span><span class="sxs-lookup"><span data-stu-id="f6c88-143">Comments</span></span>

<span data-ttu-id="f6c88-144">Všimněte si, že v předchozím příkladu privátní pole (`name` a `age`) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy.</span><span class="sxs-lookup"><span data-stu-id="f6c88-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="f6c88-145">Například nelze tisknout název podřízené tabulky z `Main` metodu, pomocí příkazu takto:</span><span class="sxs-lookup"><span data-stu-id="f6c88-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="f6c88-146">Přístup k soukromým členům `Child` z `Main` pouze by bylo možné Pokud `Main` byly člena třídy.</span><span class="sxs-lookup"><span data-stu-id="f6c88-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="f6c88-147">Typy deklarované uvnitř třídy bez výchozí modifikátor přístupu `private`, takže datových členů v tomto příkladu bude stále `private` Pokud klíčové slovo byly odebrány.</span><span class="sxs-lookup"><span data-stu-id="f6c88-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="f6c88-148">A konečně, Všimněte si, že pro objekt vytvořený pomocí výchozího konstruktoru (`child3`), věk pole bylo inicializované na nula ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f6c88-148">Finally, notice that for the object created using the default constructor (`child3`), the age field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6c88-149">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6c88-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6c88-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6c88-150">See also</span></span>

[<span data-ttu-id="f6c88-151">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6c88-151">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="f6c88-152">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f6c88-152">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="f6c88-153">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6c88-153">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="f6c88-154">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="f6c88-154">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
