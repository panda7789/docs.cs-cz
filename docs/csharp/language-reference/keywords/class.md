---
description: klíčové slovo class – Referenční dokumentace jazyka C#
title: klíčové slovo class – Referenční dokumentace jazyka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 67c9c4be55cce25edf9ecb84b257a8523f193bec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142112"
---
# <a name="class-c-reference"></a><span data-ttu-id="31829-103">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="31829-103">class (C# Reference)</span></span>

<span data-ttu-id="31829-104">Třídy jsou deklarovány pomocí klíčového slova `class` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="31829-104">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="31829-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31829-105">Remarks</span></span>

<span data-ttu-id="31829-106">V jazyce C# je povolena pouze jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="31829-106">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="31829-107">Jinými slovy třída může dědit pouze implementaci pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="31829-107">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="31829-108">Třída však může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31829-108">However, a class can implement more than one interface.</span></span> <span data-ttu-id="31829-109">V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="31829-109">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="31829-110">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="31829-110">Inheritance</span></span>|<span data-ttu-id="31829-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="31829-111">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="31829-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="31829-112">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="31829-113">Jednoduché</span><span class="sxs-lookup"><span data-stu-id="31829-113">Single</span></span>|`class DerivedClass : BaseClass { }`|
|<span data-ttu-id="31829-114">Žádné, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="31829-114">None, implements two interfaces</span></span>|`class ImplClass : IFace1, IFace2 { }`|
|<span data-ttu-id="31829-115">Single, implementuje jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31829-115">Single, implements one interface</span></span>|`class ImplDerivedClass : BaseClass, IFace1 { }`|

<span data-ttu-id="31829-116">Třídy, které deklarujete přímo v rámci oboru názvů, nikoli vnořené v rámci jiných tříd, mohou být buď [veřejné](./public.md) , nebo [interní](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="31829-116">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="31829-117">Třídy jsou `internal` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="31829-117">Classes are `internal` by default.</span></span>

<span data-ttu-id="31829-118">Členy třídy, včetně vnořených tříd, mohou být [Veřejná](public.md), [chráněná interní](protected-internal.md), [chráněná](protected.md), [interní](internal.md), [soukromá](private.md)nebo [soukromá](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="31829-118">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="31829-119">Členy jsou `private` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="31829-119">Members are `private` by default.</span></span>

<span data-ttu-id="31829-120">Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="31829-120">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="31829-121">Můžete deklarovat obecné třídy, které mají parametry typu.</span><span class="sxs-lookup"><span data-stu-id="31829-121">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="31829-122">Další informace naleznete v tématu [Obecné třídy](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="31829-122">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="31829-123">Třída může obsahovat deklarace následujících členů:</span><span class="sxs-lookup"><span data-stu-id="31829-123">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="31829-124">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="31829-124">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="31829-125">Konstanty</span><span class="sxs-lookup"><span data-stu-id="31829-125">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="31829-126">Pole</span><span class="sxs-lookup"><span data-stu-id="31829-126">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="31829-127">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="31829-127">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="31829-128">Metody</span><span class="sxs-lookup"><span data-stu-id="31829-128">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="31829-129">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="31829-129">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="31829-130">Indexery</span><span class="sxs-lookup"><span data-stu-id="31829-130">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="31829-131">Operátory</span><span class="sxs-lookup"><span data-stu-id="31829-131">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="31829-132">Události</span><span class="sxs-lookup"><span data-stu-id="31829-132">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="31829-133">Delegáti</span><span class="sxs-lookup"><span data-stu-id="31829-133">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="31829-134">Třídy</span><span class="sxs-lookup"><span data-stu-id="31829-134">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="31829-135">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="31829-135">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="31829-136">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="31829-136">Structure types</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="31829-137">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="31829-137">Enumeration types</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="31829-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="31829-138">Example</span></span>

<span data-ttu-id="31829-139">Následující příklad ukazuje deklaraci polí třídy, konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="31829-139">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="31829-140">Ukazuje také vytváření instancí objektů a data instance tisku.</span><span class="sxs-lookup"><span data-stu-id="31829-140">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="31829-141">V tomto příkladu jsou deklarovány dvě třídy.</span><span class="sxs-lookup"><span data-stu-id="31829-141">In this example, two classes are declared.</span></span> <span data-ttu-id="31829-142">První třída `Child` obsahuje dvě soukromá pole ( `name` a `age` ), dva veřejné konstruktory a jednu veřejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="31829-142">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="31829-143">Druhá třída, `StringTest` ,,, je použita k zahrnutí `Main` .</span><span class="sxs-lookup"><span data-stu-id="31829-143">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="31829-144">Komentáře</span><span class="sxs-lookup"><span data-stu-id="31829-144">Comments</span></span>

<span data-ttu-id="31829-145">Všimněte si, že v předchozím příkladu k soukromým polím ( `name` a `age` ) lze přistupovat pouze prostřednictvím veřejné metody `Child` třídy.</span><span class="sxs-lookup"><span data-stu-id="31829-145">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="31829-146">Nemůžete například vytisknout název podřízeného objektu z `Main` metody pomocí příkazu, například takto:</span><span class="sxs-lookup"><span data-stu-id="31829-146">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="31829-147">Přístup k soukromým členům `Child` z `Main` by byl možný pouze v případě, že `Main` byl členem třídy.</span><span class="sxs-lookup"><span data-stu-id="31829-147">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="31829-148">Typy deklarované uvnitř třídy bez modifikátoru přístupu výchozí pro `private` , takže datové členy v tomto příkladu budou pořád i v `private` případě, že se klíčové slovo odebralo.</span><span class="sxs-lookup"><span data-stu-id="31829-148">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="31829-149">Nakonec si všimněte, že pro objekt vytvořený pomocí konstruktoru bez parametrů ( `child3` ) `age` bylo ve výchozím nastavení inicializováno pole nula.</span><span class="sxs-lookup"><span data-stu-id="31829-149">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="31829-150">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31829-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="31829-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="31829-151">See also</span></span>

- [<span data-ttu-id="31829-152">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31829-152">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31829-153">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="31829-153">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31829-154">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31829-154">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="31829-155">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="31829-155">Reference Types</span></span>](./reference-types.md)
