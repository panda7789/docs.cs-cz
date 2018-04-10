---
title: Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44d065429f67d717d7c50e3877294eadd462a99d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="bcf01-102">Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bcf01-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="bcf01-103">Když zadáte v deklaraci typu, zkontrolujte, zda usnadnění úroveň tohoto typu je závislé na úrovni přístupu člena nebo jiného typu.</span><span class="sxs-lookup"><span data-stu-id="bcf01-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="bcf01-104">Například přímé základní třídu, musí být dostupné jako odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="bcf01-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="bcf01-105">Následující deklarace způsobit chyby kompilátoru, protože základní třída `BaseClass` je méně přístupný než `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="bcf01-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="bcf01-106">Následující tabulka shrnuje omezení na úrovní deklarované přístupu.</span><span class="sxs-lookup"><span data-stu-id="bcf01-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="bcf01-107">Kontext</span><span class="sxs-lookup"><span data-stu-id="bcf01-107">Context</span></span>|<span data-ttu-id="bcf01-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcf01-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="bcf01-109">Třídy</span><span class="sxs-lookup"><span data-stu-id="bcf01-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="bcf01-110">Základní třídy přímé typu třídy musí být dostupné jako typ třídy.</span><span class="sxs-lookup"><span data-stu-id="bcf01-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="bcf01-111">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcf01-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="bcf01-112">Rozhraní explicitní základní typ rozhraní musí být dostupné jako vlastní typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bcf01-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="bcf01-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="bcf01-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="bcf01-114">Návratový typ a typy parametrů typu delegáta musí být dostupné jako vlastní typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="bcf01-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="bcf01-115">Konstanty</span><span class="sxs-lookup"><span data-stu-id="bcf01-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="bcf01-116">Typ konstanty musí být dostupné jako konstanta sám sebe.</span><span class="sxs-lookup"><span data-stu-id="bcf01-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="bcf01-117">Pole</span><span class="sxs-lookup"><span data-stu-id="bcf01-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="bcf01-118">Typ pole musí být dostupné jako vlastní pole.</span><span class="sxs-lookup"><span data-stu-id="bcf01-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="bcf01-119">Metody</span><span class="sxs-lookup"><span data-stu-id="bcf01-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="bcf01-120">Návratový typ a typy parametrů metody musí být přístupné metoda sama.</span><span class="sxs-lookup"><span data-stu-id="bcf01-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="bcf01-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bcf01-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="bcf01-122">Typ vlastnosti musí být dostupné jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bcf01-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="bcf01-123">Události</span><span class="sxs-lookup"><span data-stu-id="bcf01-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="bcf01-124">Typ události musí být dostupné jako samotné události.</span><span class="sxs-lookup"><span data-stu-id="bcf01-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="bcf01-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="bcf01-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="bcf01-126">Typ a parametr typy indexer musí být dostupné jako indexeru sám sebe.</span><span class="sxs-lookup"><span data-stu-id="bcf01-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="bcf01-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="bcf01-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="bcf01-128">Návratový typ a typy parametrů operátoru musí být dostupné jako operátor.</span><span class="sxs-lookup"><span data-stu-id="bcf01-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="bcf01-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="bcf01-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="bcf01-130">Typy parametrů konstruktor musí být dostupné jako konstruktoru sám sebe.</span><span class="sxs-lookup"><span data-stu-id="bcf01-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bcf01-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcf01-131">Example</span></span>  
 <span data-ttu-id="bcf01-132">Následující příklad obsahuje chybné deklarace různých typů.</span><span class="sxs-lookup"><span data-stu-id="bcf01-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="bcf01-133">Komentář následující každá deklarace značí chybu očekávané kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bcf01-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
```  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="bcf01-134">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcf01-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bcf01-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcf01-135">See Also</span></span>  
 [<span data-ttu-id="bcf01-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcf01-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bcf01-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bcf01-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bcf01-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcf01-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bcf01-139">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="bcf01-139">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="bcf01-140">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="bcf01-140">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="bcf01-141">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="bcf01-141">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="bcf01-142">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="bcf01-142">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="bcf01-143">veřejné</span><span class="sxs-lookup"><span data-stu-id="bcf01-143">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="bcf01-144">privátní</span><span class="sxs-lookup"><span data-stu-id="bcf01-144">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="bcf01-145">chráněný</span><span class="sxs-lookup"><span data-stu-id="bcf01-145">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="bcf01-146">interní</span><span class="sxs-lookup"><span data-stu-id="bcf01-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
