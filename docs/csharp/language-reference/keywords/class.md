---
title: klíčové slovo třídy C# – referenční informace
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 506cc3b86961ca22361d37d372bcac9632528cae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602229"
---
# <a name="class-c-reference"></a><span data-ttu-id="eaf46-102">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eaf46-102">class (C# Reference)</span></span>

<span data-ttu-id="eaf46-103">Třídy jsou deklarovány pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="eaf46-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="eaf46-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaf46-104">Remarks</span></span>

<span data-ttu-id="eaf46-105">V C#je povolena pouze jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="eaf46-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="eaf46-106">Jinými slovy třída může dědit pouze implementaci pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="eaf46-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="eaf46-107">Třída však může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eaf46-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="eaf46-108">V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="eaf46-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="eaf46-109">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="eaf46-109">Inheritance</span></span>|<span data-ttu-id="eaf46-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="eaf46-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="eaf46-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="eaf46-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="eaf46-112">Single</span><span class="sxs-lookup"><span data-stu-id="eaf46-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="eaf46-113">Žádné, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaf46-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="eaf46-114">Single, implementuje jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eaf46-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="eaf46-115">Třídy, které deklarujete přímo v rámci oboru názvů, nikoli vnořené v rámci jiných tříd, mohou být buď [veřejné](./public.md) , nebo [interní](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="eaf46-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="eaf46-116">Třídy jsou `internal` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="eaf46-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="eaf46-117">Členy třídy, včetně vnořených tříd, mohou [být veřejná](public.md), [chráněná interní](protected-internal.md), [chráněná](protected.md), [interní](internal.md), [soukromá](private.md)nebo [soukromá](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="eaf46-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="eaf46-118">Členy jsou `private` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="eaf46-118">Members are `private` by default.</span></span>

<span data-ttu-id="eaf46-119">Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="eaf46-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="eaf46-120">Můžete deklarovat obecné třídy, které mají parametry typu.</span><span class="sxs-lookup"><span data-stu-id="eaf46-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="eaf46-121">Další informace naleznete v tématu [Obecné třídy](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="eaf46-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="eaf46-122">Třída může obsahovat deklarace následujících členů:</span><span class="sxs-lookup"><span data-stu-id="eaf46-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="eaf46-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="eaf46-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="eaf46-124">Konstanty</span><span class="sxs-lookup"><span data-stu-id="eaf46-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="eaf46-125">Pole</span><span class="sxs-lookup"><span data-stu-id="eaf46-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="eaf46-126">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="eaf46-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="eaf46-127">Metody</span><span class="sxs-lookup"><span data-stu-id="eaf46-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="eaf46-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="eaf46-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="eaf46-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="eaf46-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="eaf46-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="eaf46-130">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)

- [<span data-ttu-id="eaf46-131">Události</span><span class="sxs-lookup"><span data-stu-id="eaf46-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="eaf46-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="eaf46-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="eaf46-133">Třídy</span><span class="sxs-lookup"><span data-stu-id="eaf46-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="eaf46-134">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaf46-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="eaf46-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="eaf46-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="eaf46-136">Výčty</span><span class="sxs-lookup"><span data-stu-id="eaf46-136">Enumerations</span></span>](../../programming-guide/enumeration-types.md)

## <a name="example"></a><span data-ttu-id="eaf46-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="eaf46-137">Example</span></span>

<span data-ttu-id="eaf46-138">Následující příklad ukazuje deklaraci polí třídy, konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="eaf46-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="eaf46-139">Ukazuje také vytváření instancí objektů a data instance tisku.</span><span class="sxs-lookup"><span data-stu-id="eaf46-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="eaf46-140">V tomto příkladu jsou deklarovány dvě třídy.</span><span class="sxs-lookup"><span data-stu-id="eaf46-140">In this example, two classes are declared.</span></span> <span data-ttu-id="eaf46-141">První třída `Child`obsahuje dvě soukromá pole (`name` a `age`), dva veřejné konstruktory a jednu veřejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="eaf46-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="eaf46-142">Druhá třída, `StringTest`,,, je použita k `Main`zahrnutí.</span><span class="sxs-lookup"><span data-stu-id="eaf46-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="eaf46-143">Komentáře</span><span class="sxs-lookup"><span data-stu-id="eaf46-143">Comments</span></span>

<span data-ttu-id="eaf46-144">Všimněte si, že v předchozím příkladu k soukromým`name` polím `age`(a) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy.</span><span class="sxs-lookup"><span data-stu-id="eaf46-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="eaf46-145">Nemůžete například vytisknout název podřízeného objektu z `Main` metody pomocí příkazu, například takto:</span><span class="sxs-lookup"><span data-stu-id="eaf46-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="eaf46-146">Přístup k soukromým `Child` členům `Main` z by byl možný pouze `Main` v případě, že byl členem třídy.</span><span class="sxs-lookup"><span data-stu-id="eaf46-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="eaf46-147">Typy deklarované uvnitř třídy bez modifikátoru přístupu výchozí pro `private`, takže datové členy v tomto příkladu budou `private` pořád i v případě, že se klíčové slovo odebralo.</span><span class="sxs-lookup"><span data-stu-id="eaf46-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="eaf46-148">Nakonec si všimněte, že pro objekt vytvořený pomocí konstruktoru bez parametrů (`child3`) `age` bylo ve výchozím nastavení inicializováno pole nula.</span><span class="sxs-lookup"><span data-stu-id="eaf46-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eaf46-149">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eaf46-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eaf46-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaf46-150">See also</span></span>

- [<span data-ttu-id="eaf46-151">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="eaf46-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eaf46-152">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="eaf46-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eaf46-153">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eaf46-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="eaf46-154">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="eaf46-154">Reference Types</span></span>](./reference-types.md)
