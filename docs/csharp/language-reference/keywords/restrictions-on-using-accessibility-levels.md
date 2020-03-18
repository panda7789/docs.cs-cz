---
title: Omezení používání úrovní usnadnění – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173533"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="84fc6-102">Omezení používání úrovní usnadnění (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="84fc6-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="84fc6-103">Když zadáte typ v deklaraci, zkontrolujte, zda úroveň usnadnění typu je závislá na úrovni usnadnění přístupu člena nebo jiného typu.</span><span class="sxs-lookup"><span data-stu-id="84fc6-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="84fc6-104">Například přímá základní třída musí být alespoň stejně přístupná jako odvozená třída.</span><span class="sxs-lookup"><span data-stu-id="84fc6-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="84fc6-105">Následující deklarace způsobit chybu kompilátoru, protože základní třída `BaseClass` je méně přístupné než `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="84fc6-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="84fc6-106">Následující tabulka shrnuje omezení deklarovaných úrovní usnadnění.</span><span class="sxs-lookup"><span data-stu-id="84fc6-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="84fc6-107">Kontext</span><span class="sxs-lookup"><span data-stu-id="84fc6-107">Context</span></span>|<span data-ttu-id="84fc6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84fc6-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="84fc6-109">Třídy</span><span class="sxs-lookup"><span data-stu-id="84fc6-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="84fc6-110">Přímá základní třída typu třídy musí být alespoň stejně přístupná jako samotný typ třídy.</span><span class="sxs-lookup"><span data-stu-id="84fc6-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="84fc6-111">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="84fc6-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="84fc6-112">Explicitní základní rozhraní typu rozhraní musí být alespoň stejně přístupné jako samotný typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="84fc6-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="84fc6-113">Delegáty</span><span class="sxs-lookup"><span data-stu-id="84fc6-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="84fc6-114">Návratový typ a typy parametrů typu delegáta musí být alespoň stejně přístupné jako samotný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="84fc6-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="84fc6-115">Konstanty</span><span class="sxs-lookup"><span data-stu-id="84fc6-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="84fc6-116">Typ konstanty musí být alespoň stejně přístupný jako konstanta sama.</span><span class="sxs-lookup"><span data-stu-id="84fc6-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="84fc6-117">Pole</span><span class="sxs-lookup"><span data-stu-id="84fc6-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="84fc6-118">Typ pole musí být alespoň stejně přístupný jako samotné pole.</span><span class="sxs-lookup"><span data-stu-id="84fc6-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="84fc6-119">Metody</span><span class="sxs-lookup"><span data-stu-id="84fc6-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="84fc6-120">Návratový typ a typy parametrů metody musí být alespoň stejně přístupné jako samotná metoda.</span><span class="sxs-lookup"><span data-stu-id="84fc6-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="84fc6-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="84fc6-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="84fc6-122">Typ vlastnosti musí být alespoň stejně přístupný jako vlastnost sama.</span><span class="sxs-lookup"><span data-stu-id="84fc6-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="84fc6-123">Akce</span><span class="sxs-lookup"><span data-stu-id="84fc6-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="84fc6-124">Typ události musí být alespoň stejně přístupný jako samotná událost.</span><span class="sxs-lookup"><span data-stu-id="84fc6-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="84fc6-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="84fc6-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="84fc6-126">Typy typů a parametrů indexeru musí být alespoň stejně přístupné jako indexer sám.</span><span class="sxs-lookup"><span data-stu-id="84fc6-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="84fc6-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="84fc6-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="84fc6-128">Návratový typ a typy parametrů operátoru musí být alespoň stejně přístupné jako samotný operátor.</span><span class="sxs-lookup"><span data-stu-id="84fc6-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="84fc6-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="84fc6-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="84fc6-130">Typy parametrů konstruktoru musí být alespoň stejně přístupné jako samotný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="84fc6-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="84fc6-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="84fc6-131">Example</span></span>

<span data-ttu-id="84fc6-132">Následující příklad obsahuje chybné deklarace různých typů.</span><span class="sxs-lookup"><span data-stu-id="84fc6-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="84fc6-133">Komentář za každou deklarací označuje očekávanou chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="84fc6-133">The comment following each declaration indicates the expected compiler error.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="84fc6-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84fc6-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="84fc6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="84fc6-135">See also</span></span>

- [<span data-ttu-id="84fc6-136">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84fc6-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="84fc6-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84fc6-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="84fc6-138">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="84fc6-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="84fc6-139">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="84fc6-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="84fc6-140">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="84fc6-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="84fc6-141">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="84fc6-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="84fc6-142">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="84fc6-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="84fc6-143">Veřejné</span><span class="sxs-lookup"><span data-stu-id="84fc6-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="84fc6-144">Soukromé</span><span class="sxs-lookup"><span data-stu-id="84fc6-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="84fc6-145">protected</span><span class="sxs-lookup"><span data-stu-id="84fc6-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="84fc6-146">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="84fc6-146">internal</span></span>](../../language-reference/keywords/internal.md)
