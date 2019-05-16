---
title: Omezení používání pro usnadnění úrovně - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 3a5915d23fea02a031cedd9063018fffbdc34180
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633779"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="5106e-102">Omezení používání úrovní přístupu (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5106e-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="5106e-103">Při zadávání typu v deklaraci, zkontrolujte, zda úroveň přístupnost typu je závislé na úrovni přístupu člena nebo jiného typu.</span><span class="sxs-lookup"><span data-stu-id="5106e-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="5106e-104">Například přímou základní třídu, musí být přinejmenším stejně dostupná jako odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5106e-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="5106e-105">Následující deklarace způsobí chybu kompilátoru, protože základní třída `BaseClass` je méně dostupný než `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="5106e-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="5106e-106">Následující tabulka shrnuje omezení úrovní deklarovaná přístupnost.</span><span class="sxs-lookup"><span data-stu-id="5106e-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="5106e-107">Kontext</span><span class="sxs-lookup"><span data-stu-id="5106e-107">Context</span></span>|<span data-ttu-id="5106e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5106e-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="5106e-109">Třídy</span><span class="sxs-lookup"><span data-stu-id="5106e-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="5106e-110">Přímou základní třídu typu třídy musí být přinejmenším stejně dostupná jako typ třídy.</span><span class="sxs-lookup"><span data-stu-id="5106e-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="5106e-111">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="5106e-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="5106e-112">Explicitní základní rozhraní typu rozhraní musí být přinejmenším stejně dostupná jako samotného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5106e-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="5106e-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="5106e-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="5106e-114">Návratový typ a typy parametrů typu delegáta musí být přinejmenším stejně dostupná jako samotného typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="5106e-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="5106e-115">Konstanty</span><span class="sxs-lookup"><span data-stu-id="5106e-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="5106e-116">Typ konstanty musí být přinejmenším stejně dostupná jako konstanta samotný.</span><span class="sxs-lookup"><span data-stu-id="5106e-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="5106e-117">Pole</span><span class="sxs-lookup"><span data-stu-id="5106e-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="5106e-118">Typ pole musí být přinejmenším stejně dostupná jako vlastní pole.</span><span class="sxs-lookup"><span data-stu-id="5106e-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="5106e-119">Metody</span><span class="sxs-lookup"><span data-stu-id="5106e-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="5106e-120">Návratový typ a typy parametrů metody musí být přinejmenším stejně dostupná jako metoda sama.</span><span class="sxs-lookup"><span data-stu-id="5106e-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="5106e-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5106e-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="5106e-122">Typ vlastnosti musí být přinejmenším stejně dostupná jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5106e-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="5106e-123">Události</span><span class="sxs-lookup"><span data-stu-id="5106e-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="5106e-124">Typ události musí být přinejmenším stejně dostupná jako samotné události.</span><span class="sxs-lookup"><span data-stu-id="5106e-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="5106e-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="5106e-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="5106e-126">Typ a parametrem typy indexer musí být přinejmenším stejně dostupná jako samotný indexeru.</span><span class="sxs-lookup"><span data-stu-id="5106e-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="5106e-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="5106e-127">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="5106e-128">Návratový typ a typy parametrů operátoru musí být přinejmenším stejně dostupná jako operátor.</span><span class="sxs-lookup"><span data-stu-id="5106e-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="5106e-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="5106e-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="5106e-130">Typy parametrů konstruktoru musí být přinejmenším stejně dostupná jako konstruktor samotný.</span><span class="sxs-lookup"><span data-stu-id="5106e-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="5106e-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="5106e-131">Example</span></span>

<span data-ttu-id="5106e-132">Následující příklad obsahuje chybné deklarace různých typů.</span><span class="sxs-lookup"><span data-stu-id="5106e-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="5106e-133">Komentář po deklaraci označuje chybu kompilátoru očekávané.</span><span class="sxs-lookup"><span data-stu-id="5106e-133">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible 
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error: 
    // "The parameter B.MyPrivateMethod is not accessible due to 
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="5106e-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5106e-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5106e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5106e-135">See also</span></span>

- [<span data-ttu-id="5106e-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5106e-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="5106e-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5106e-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5106e-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5106e-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="5106e-139">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="5106e-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="5106e-140">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="5106e-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="5106e-141">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="5106e-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="5106e-142">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="5106e-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="5106e-143">public</span><span class="sxs-lookup"><span data-stu-id="5106e-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="5106e-144">private</span><span class="sxs-lookup"><span data-stu-id="5106e-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="5106e-145">protected</span><span class="sxs-lookup"><span data-stu-id="5106e-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="5106e-146">internal</span><span class="sxs-lookup"><span data-stu-id="5106e-146">internal</span></span>](../../language-reference/keywords/internal.md)
