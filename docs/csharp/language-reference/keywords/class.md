---
title: klíčové slovo třídy – odkaz jazyka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673092"
---
# <a name="class-c-reference"></a><span data-ttu-id="dc734-102">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dc734-102">class (C# Reference)</span></span>

<span data-ttu-id="dc734-103">Třídy jsou deklarovány pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dc734-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="dc734-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc734-104">Remarks</span></span>

<span data-ttu-id="dc734-105">V c#.</span><span class="sxs-lookup"><span data-stu-id="dc734-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="dc734-106">Jinými slovy, třída může dědit implementaci pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="dc734-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="dc734-107">Třída však může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dc734-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="dc734-108">V následující tabulce jsou uvedeny příklady dědičnosti třídy a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="dc734-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="dc734-109">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="dc734-109">Inheritance</span></span>|<span data-ttu-id="dc734-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc734-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="dc734-111">Žádný</span><span class="sxs-lookup"><span data-stu-id="dc734-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="dc734-112">Single</span><span class="sxs-lookup"><span data-stu-id="dc734-112">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="dc734-113">Žádné, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc734-113">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="dc734-114">Jediné, implementuje jedno rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc734-114">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="dc734-115">Třídy, které deklarujete přímo v oboru názvů, nikoli vnořené do jiných tříd, mohou být [veřejné](./public.md) nebo [interní](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="dc734-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="dc734-116">Třídy `internal` jsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc734-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="dc734-117">Členové třídy, včetně vnořených tříd, mohou být [veřejné](public.md), [chráněné vnitřní](protected-internal.md), [chráněné](protected.md), [interní](internal.md), [soukromé](private.md)nebo [soukromé chráněné](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="dc734-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="dc734-118">Členové `private` jsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dc734-118">Members are `private` by default.</span></span>

<span data-ttu-id="dc734-119">Další informace naleznete [v tématu Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="dc734-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="dc734-120">Můžete deklarovat obecné třídy, které mají parametry typu.</span><span class="sxs-lookup"><span data-stu-id="dc734-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="dc734-121">Další informace naleznete [v tématu Obecné třídy](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="dc734-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="dc734-122">Třída může obsahovat deklarace následujících členů:</span><span class="sxs-lookup"><span data-stu-id="dc734-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="dc734-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="dc734-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="dc734-124">Konstanty</span><span class="sxs-lookup"><span data-stu-id="dc734-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="dc734-125">Pole</span><span class="sxs-lookup"><span data-stu-id="dc734-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="dc734-126">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="dc734-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="dc734-127">Metody</span><span class="sxs-lookup"><span data-stu-id="dc734-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="dc734-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc734-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="dc734-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="dc734-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="dc734-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="dc734-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="dc734-131">Akce</span><span class="sxs-lookup"><span data-stu-id="dc734-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="dc734-132">Delegáty</span><span class="sxs-lookup"><span data-stu-id="dc734-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="dc734-133">Třídy</span><span class="sxs-lookup"><span data-stu-id="dc734-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="dc734-134">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc734-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="dc734-135">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="dc734-135">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="dc734-136">Typy výčtu</span><span class="sxs-lookup"><span data-stu-id="dc734-136">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="dc734-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc734-137">Example</span></span>

<span data-ttu-id="dc734-138">Následující příklad ukazuje deklarování polí třídy, konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="dc734-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="dc734-139">Také ukazuje instanciontace objektu a tisk instancí dat.</span><span class="sxs-lookup"><span data-stu-id="dc734-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="dc734-140">V tomto příkladu jsou deklarovány dvě třídy.</span><span class="sxs-lookup"><span data-stu-id="dc734-140">In this example, two classes are declared.</span></span> <span data-ttu-id="dc734-141">První třída `Child`, obsahuje dvě`name` soukromá pole ( a `age`), dva veřejné konstruktory a jednu veřejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="dc734-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="dc734-142">Druhá třída `StringTest`, se používá `Main`k obsahují .</span><span class="sxs-lookup"><span data-stu-id="dc734-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="dc734-143">Komentáře</span><span class="sxs-lookup"><span data-stu-id="dc734-143">Comments</span></span>

<span data-ttu-id="dc734-144">Všimněte si, že v`name` předchozím `age`příkladu soukromé pole ( a `Child` ) lze přistupovat pouze prostřednictvím veřejné metody třídy.</span><span class="sxs-lookup"><span data-stu-id="dc734-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="dc734-145">Například nelze vytisknout název dítěte, z `Main` metody, pomocí příkazu, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="dc734-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="dc734-146">Přístup k soukromým `Child` `Main` členům z `Main` by bylo možné pouze v případě, že by byli členy třídy.</span><span class="sxs-lookup"><span data-stu-id="dc734-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="dc734-147">Typy deklarované uvnitř třídy `private`bez modifikátoru přístupu `private` ve výchozím nastavení , takže datové členy v tomto příkladu by stále bylo, pokud klíčové slovo byly odebrány.</span><span class="sxs-lookup"><span data-stu-id="dc734-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="dc734-148">Nakonec si všimněte, že pro objekt vytvořený`child3`pomocí `age` konstruktoru bez parametrů ( ), bylo pole ve výchozím nastavení inicializováno na nulu.</span><span class="sxs-lookup"><span data-stu-id="dc734-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc734-149">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc734-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dc734-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc734-150">See also</span></span>

- [<span data-ttu-id="dc734-151">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc734-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dc734-152">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc734-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dc734-153">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="dc734-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="dc734-154">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="dc734-154">Reference Types</span></span>](./reference-types.md)
