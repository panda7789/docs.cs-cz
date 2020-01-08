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
ms.openlocfilehash: 61f15550482e8499e57197e35970e7ec8a096947
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345508"
---
# <a name="class-c-reference"></a><span data-ttu-id="b0f5b-102">class (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b0f5b-102">class (C# Reference)</span></span>

<span data-ttu-id="b0f5b-103">Třídy jsou deklarovány pomocí klíčového slova `class`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b0f5b-103">Classes are declared using the keyword `class`, as shown in the following example:</span></span>

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a><span data-ttu-id="b0f5b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0f5b-104">Remarks</span></span>

<span data-ttu-id="b0f5b-105">V C#je povolena pouze jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-105">Only single inheritance is allowed in C#.</span></span> <span data-ttu-id="b0f5b-106">Jinými slovy třída může dědit pouze implementaci pouze z jedné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-106">In other words, a class can inherit implementation from one base class only.</span></span> <span data-ttu-id="b0f5b-107">Třída však může implementovat více než jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-107">However, a class can implement more than one interface.</span></span> <span data-ttu-id="b0f5b-108">V následující tabulce jsou uvedeny příklady dědičnosti tříd a implementace rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b0f5b-108">The following table shows examples of class inheritance and interface implementation:</span></span>

|<span data-ttu-id="b0f5b-109">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="b0f5b-109">Inheritance</span></span>|<span data-ttu-id="b0f5b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0f5b-110">Example</span></span>|
|-----------------|-------------|
|<span data-ttu-id="b0f5b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="b0f5b-111">None</span></span>|`class ClassA { }`|
|<span data-ttu-id="b0f5b-112">Jednoduché</span><span class="sxs-lookup"><span data-stu-id="b0f5b-112">Single</span></span>|`class DerivedClass: BaseClass { }`|
|<span data-ttu-id="b0f5b-113">Žádné, implementuje dvě rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0f5b-113">None, implements two interfaces</span></span>|`class ImplClass: IFace1, IFace2 { }`|
|<span data-ttu-id="b0f5b-114">Single, implementuje jedno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-114">Single, implements one interface</span></span>|`class ImplDerivedClass: BaseClass, IFace1 { }`|

<span data-ttu-id="b0f5b-115">Třídy, které deklarujete přímo v rámci oboru názvů, nikoli vnořené v rámci jiných tříd, mohou být buď [veřejné](./public.md) , nebo [interní](./internal.md).</span><span class="sxs-lookup"><span data-stu-id="b0f5b-115">Classes that you declare directly within a namespace, not nested within other classes, can be either [public](./public.md) or [internal](./internal.md).</span></span> <span data-ttu-id="b0f5b-116">Třídy jsou ve výchozím nastavení `internal`.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-116">Classes are `internal` by default.</span></span>

<span data-ttu-id="b0f5b-117">Členy třídy, včetně vnořených tříd, mohou být [Veřejná](public.md), [chráněná interní](protected-internal.md), [chráněná](protected.md), [interní](internal.md), [soukromá](private.md)nebo [soukromá](private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="b0f5b-117">Class members, including nested classes, can be [public](public.md), [protected internal](protected-internal.md), [protected](protected.md), [internal](internal.md), [private](private.md), or [private protected](private-protected.md).</span></span> <span data-ttu-id="b0f5b-118">Ve výchozím nastavení jsou členy `private`.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-118">Members are `private` by default.</span></span>

<span data-ttu-id="b0f5b-119">Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b0f5b-119">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

<span data-ttu-id="b0f5b-120">Můžete deklarovat obecné třídy, které mají parametry typu.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-120">You can declare generic classes that have type parameters.</span></span> <span data-ttu-id="b0f5b-121">Další informace naleznete v tématu [Obecné třídy](../../programming-guide/generics/generic-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b0f5b-121">For more information, see [Generic Classes](../../programming-guide/generics/generic-classes.md).</span></span>

<span data-ttu-id="b0f5b-122">Třída může obsahovat deklarace následujících členů:</span><span class="sxs-lookup"><span data-stu-id="b0f5b-122">A class can contain declarations of the following members:</span></span>

- [<span data-ttu-id="b0f5b-123">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="b0f5b-123">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)

- [<span data-ttu-id="b0f5b-124">Konstanty</span><span class="sxs-lookup"><span data-stu-id="b0f5b-124">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)

- [<span data-ttu-id="b0f5b-125">Pole</span><span class="sxs-lookup"><span data-stu-id="b0f5b-125">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)

- [<span data-ttu-id="b0f5b-126">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="b0f5b-126">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)

- [<span data-ttu-id="b0f5b-127">Metody</span><span class="sxs-lookup"><span data-stu-id="b0f5b-127">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="b0f5b-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b0f5b-128">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)

- [<span data-ttu-id="b0f5b-129">Indexery</span><span class="sxs-lookup"><span data-stu-id="b0f5b-129">Indexers</span></span>](../../programming-guide/indexers/index.md)

- [<span data-ttu-id="b0f5b-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="b0f5b-130">Operators</span></span>](../operators/index.md)

- [<span data-ttu-id="b0f5b-131">Události</span><span class="sxs-lookup"><span data-stu-id="b0f5b-131">Events</span></span>](../../programming-guide/events/index.md)

- [<span data-ttu-id="b0f5b-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="b0f5b-132">Delegates</span></span>](../../programming-guide/delegates/index.md)

- [<span data-ttu-id="b0f5b-133">Třídy</span><span class="sxs-lookup"><span data-stu-id="b0f5b-133">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)

- [<span data-ttu-id="b0f5b-134">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0f5b-134">Interfaces</span></span>](../../programming-guide/interfaces/index.md)

- [<span data-ttu-id="b0f5b-135">Struktury</span><span class="sxs-lookup"><span data-stu-id="b0f5b-135">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)

- [<span data-ttu-id="b0f5b-136">Výčty</span><span class="sxs-lookup"><span data-stu-id="b0f5b-136">Enumerations</span></span>](../builtin-types/enum.md)

## <a name="example"></a><span data-ttu-id="b0f5b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0f5b-137">Example</span></span>

<span data-ttu-id="b0f5b-138">Následující příklad ukazuje deklaraci polí třídy, konstruktorů a metod.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-138">The following example demonstrates declaring class fields, constructors, and methods.</span></span> <span data-ttu-id="b0f5b-139">Ukazuje také vytváření instancí objektů a data instance tisku.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-139">It also demonstrates object instantiation and printing instance data.</span></span> <span data-ttu-id="b0f5b-140">V tomto příkladu jsou deklarovány dvě třídy.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-140">In this example, two classes are declared.</span></span> <span data-ttu-id="b0f5b-141">První třída, `Child`, obsahuje dvě soukromá pole (`name` a `age`), dva veřejné konstruktory a jedna veřejná metoda.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-141">The first class, `Child`, contains two private fields (`name` and `age`), two public constructors and one public method.</span></span> <span data-ttu-id="b0f5b-142">Druhá třída, `StringTest`, slouží k zahrnutí `Main`.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-142">The second class, `StringTest`, is used to contain `Main`.</span></span>

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a><span data-ttu-id="b0f5b-143">Komentáře</span><span class="sxs-lookup"><span data-stu-id="b0f5b-143">Comments</span></span>

<span data-ttu-id="b0f5b-144">Všimněte si, že v předchozím příkladu mohou být soukromá pole (`name` a `age`) dostupná pouze prostřednictvím veřejné metody třídy `Child`.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-144">Notice that in the previous example the private fields (`name` and `age`) can only be accessed through the public method of the `Child` class.</span></span> <span data-ttu-id="b0f5b-145">Nemůžete například vytisknout název podřízeného objektu z metody `Main` pomocí příkazu podobného tomuto:</span><span class="sxs-lookup"><span data-stu-id="b0f5b-145">For example, you cannot print the child's name, from the `Main` method, using a statement like this:</span></span>

```csharp
Console.Write(child1.name);   // Error
```

<span data-ttu-id="b0f5b-146">Přístup k soukromým členům `Child` z `Main` by byl možný pouze v případě, že `Main` byly členem třídy.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-146">Accessing private members of `Child` from `Main` would only be possible if `Main` were a member of the class.</span></span>

<span data-ttu-id="b0f5b-147">Typy deklarované uvnitř třídy bez modifikátoru přístupu `private`výchozí, takže datové členy v tomto příkladu budou nadále `private`, pokud bylo klíčové slovo odebráno.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-147">Types declared inside a class without an access modifier default to `private`, so the data members in this example would still be `private` if the keyword were removed.</span></span>

<span data-ttu-id="b0f5b-148">Nakonec si všimněte, že pro objekt vytvořený pomocí konstruktoru bez parametrů (`child3`) se ve výchozím nastavení `age` pole inicializoval jako nula.</span><span class="sxs-lookup"><span data-stu-id="b0f5b-148">Finally, notice that for the object created using the parameterless constructor (`child3`), the `age` field was initialized to zero by default.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0f5b-149">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0f5b-149">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0f5b-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0f5b-150">See also</span></span>

- [<span data-ttu-id="b0f5b-151">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b0f5b-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0f5b-152">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b0f5b-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0f5b-153">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0f5b-153">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b0f5b-154">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="b0f5b-154">Reference Types</span></span>](./reference-types.md)
