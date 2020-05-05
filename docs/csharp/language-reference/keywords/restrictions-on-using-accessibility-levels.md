---
title: Omezení používání úrovní dostupnosti – reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 8082dbd7398b6634b68f1dd2887cd55d6798a5d9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795154"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="9e15e-102">Omezení používání úrovní přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9e15e-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="9e15e-103">Při zadání typu v deklaraci ověřte, zda je úroveň přístupnosti typu závislá na úrovni přístupnosti člena nebo jiného typu.</span><span class="sxs-lookup"><span data-stu-id="9e15e-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="9e15e-104">Například Přímá základní třída musí být alespoň tak přístupná jako odvozená třída.</span><span class="sxs-lookup"><span data-stu-id="9e15e-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="9e15e-105">Následující deklarace způsobují chybu kompilátoru, protože základní třída `BaseClass` je méně dostupná než: `MyClass`</span><span class="sxs-lookup"><span data-stu-id="9e15e-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="9e15e-106">Následující tabulka shrnuje omezení deklarované úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="9e15e-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="9e15e-107">Kontext</span><span class="sxs-lookup"><span data-stu-id="9e15e-107">Context</span></span>|<span data-ttu-id="9e15e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e15e-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="9e15e-109">Třídy</span><span class="sxs-lookup"><span data-stu-id="9e15e-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="9e15e-110">Přímá základní třída typu třídy musí být alespoň tak přístupná jako typ třídy samotné.</span><span class="sxs-lookup"><span data-stu-id="9e15e-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="9e15e-111">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e15e-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="9e15e-112">Explicitní základní rozhraní typu rozhraní musí být alespoň tak přístupná jako typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e15e-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="9e15e-113">Delegáty</span><span class="sxs-lookup"><span data-stu-id="9e15e-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="9e15e-114">Návratový typ a typy parametrů typu delegáta musí být k dispozici alespoň jako typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="9e15e-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="9e15e-115">Konstanty</span><span class="sxs-lookup"><span data-stu-id="9e15e-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="9e15e-116">Typ konstanty musí být alespoň tak přístupný jako konstanta sama.</span><span class="sxs-lookup"><span data-stu-id="9e15e-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="9e15e-117">Pole</span><span class="sxs-lookup"><span data-stu-id="9e15e-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="9e15e-118">Typ pole musí být alespoň tak přístupný jako pole samotné.</span><span class="sxs-lookup"><span data-stu-id="9e15e-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="9e15e-119">Metody</span><span class="sxs-lookup"><span data-stu-id="9e15e-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="9e15e-120">Návratový typ a typy parametrů metody musí být k dispozici alespoň jako metoda samotná.</span><span class="sxs-lookup"><span data-stu-id="9e15e-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="9e15e-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9e15e-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="9e15e-122">Typ vlastnosti musí být alespoň tak přístupný jako vlastnost sama.</span><span class="sxs-lookup"><span data-stu-id="9e15e-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="9e15e-123">Události</span><span class="sxs-lookup"><span data-stu-id="9e15e-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="9e15e-124">Typ události musí být alespoň tak přístupný jako událost samotná.</span><span class="sxs-lookup"><span data-stu-id="9e15e-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="9e15e-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="9e15e-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="9e15e-126">Typy a parametry indexeru musí být alespoň tak přístupné jako indexer samotný.</span><span class="sxs-lookup"><span data-stu-id="9e15e-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="9e15e-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="9e15e-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="9e15e-128">Návratový typ a typy parametrů operátoru musí být k dispozici alespoň jako samotný operátor.</span><span class="sxs-lookup"><span data-stu-id="9e15e-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="9e15e-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9e15e-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="9e15e-130">Typy parametrů konstruktoru musí být alespoň tak přístupné jako samotný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="9e15e-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="9e15e-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e15e-131">Example</span></span>

<span data-ttu-id="9e15e-132">Následující příklad obsahuje chybné deklarace různých typů.</span><span class="sxs-lookup"><span data-stu-id="9e15e-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="9e15e-133">Komentář, který následuje za každou deklarací, indikuje očekávanou chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9e15e-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="9e15e-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e15e-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9e15e-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e15e-135">See also</span></span>

- [<span data-ttu-id="9e15e-136">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e15e-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9e15e-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9e15e-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9e15e-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e15e-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9e15e-139">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9e15e-139">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="9e15e-140">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="9e15e-140">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="9e15e-141">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="9e15e-141">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="9e15e-142">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9e15e-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="9e15e-143">public</span><span class="sxs-lookup"><span data-stu-id="9e15e-143">public</span></span>](public.md)
- [<span data-ttu-id="9e15e-144">private</span><span class="sxs-lookup"><span data-stu-id="9e15e-144">private</span></span>](private.md)
- [<span data-ttu-id="9e15e-145">protected</span><span class="sxs-lookup"><span data-stu-id="9e15e-145">protected</span></span>](protected.md)
- [<span data-ttu-id="9e15e-146">internal</span><span class="sxs-lookup"><span data-stu-id="9e15e-146">internal</span></span>](internal.md)
