---
title: Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960902"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="e6932-102">Omezení používání úrovní přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e6932-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="e6932-103">Při zadávání typu v deklaraci, zkontrolujte, zda úroveň přístupnost typu je závislé na úrovni přístupu člena nebo jiného typu.</span><span class="sxs-lookup"><span data-stu-id="e6932-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="e6932-104">Například přímou základní třídu, musí být přinejmenším stejně dostupná jako odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="e6932-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="e6932-105">Následující deklarace způsobí chybu kompilátoru, protože základní třída `BaseClass` je méně dostupný než `MyClass`:</span><span class="sxs-lookup"><span data-stu-id="e6932-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="e6932-106">Následující tabulka shrnuje omezení úrovní deklarovaná přístupnost.</span><span class="sxs-lookup"><span data-stu-id="e6932-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="e6932-107">Kontext</span><span class="sxs-lookup"><span data-stu-id="e6932-107">Context</span></span>|<span data-ttu-id="e6932-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6932-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="e6932-109">Třídy</span><span class="sxs-lookup"><span data-stu-id="e6932-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="e6932-110">Přímou základní třídu typu třídy musí být přinejmenším stejně dostupná jako typ třídy.</span><span class="sxs-lookup"><span data-stu-id="e6932-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="e6932-111">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6932-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="e6932-112">Explicitní základní rozhraní typu rozhraní musí být přinejmenším stejně dostupná jako samotného typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e6932-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="e6932-113">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e6932-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="e6932-114">Návratový typ a typy parametrů typu delegáta musí být přinejmenším stejně dostupná jako samotného typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="e6932-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="e6932-115">Konstanty</span><span class="sxs-lookup"><span data-stu-id="e6932-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="e6932-116">Typ konstanty musí být přinejmenším stejně dostupná jako konstanta samotný.</span><span class="sxs-lookup"><span data-stu-id="e6932-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="e6932-117">Pole</span><span class="sxs-lookup"><span data-stu-id="e6932-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="e6932-118">Typ pole musí být přinejmenším stejně dostupná jako vlastní pole.</span><span class="sxs-lookup"><span data-stu-id="e6932-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="e6932-119">Metody</span><span class="sxs-lookup"><span data-stu-id="e6932-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="e6932-120">Návratový typ a typy parametrů metody musí být přinejmenším stejně dostupná jako metoda sama.</span><span class="sxs-lookup"><span data-stu-id="e6932-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="e6932-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e6932-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="e6932-122">Typ vlastnosti musí být přinejmenším stejně dostupná jako samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e6932-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="e6932-123">Události</span><span class="sxs-lookup"><span data-stu-id="e6932-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="e6932-124">Typ události musí být přinejmenším stejně dostupná jako samotné události.</span><span class="sxs-lookup"><span data-stu-id="e6932-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="e6932-125">Indexery</span><span class="sxs-lookup"><span data-stu-id="e6932-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="e6932-126">Typ a parametrem typy indexer musí být přinejmenším stejně dostupná jako samotný indexeru.</span><span class="sxs-lookup"><span data-stu-id="e6932-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="e6932-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="e6932-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="e6932-128">Návratový typ a typy parametrů operátoru musí být přinejmenším stejně dostupná jako operátor.</span><span class="sxs-lookup"><span data-stu-id="e6932-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="e6932-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e6932-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="e6932-130">Typy parametrů konstruktoru musí být přinejmenším stejně dostupná jako konstruktor samotný.</span><span class="sxs-lookup"><span data-stu-id="e6932-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6932-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6932-131">Example</span></span>  
 <span data-ttu-id="e6932-132">Následující příklad obsahuje chybné deklarace různých typů.</span><span class="sxs-lookup"><span data-stu-id="e6932-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="e6932-133">Komentář po deklaraci označuje chybu kompilátoru očekávané.</span><span class="sxs-lookup"><span data-stu-id="e6932-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="e6932-134">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6932-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6932-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6932-135">See Also</span></span>  
 [<span data-ttu-id="e6932-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6932-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e6932-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e6932-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e6932-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6932-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e6932-139">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="e6932-139">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="e6932-140">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="e6932-140">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="e6932-141">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="e6932-141">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="e6932-142">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="e6932-142">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="e6932-143">public</span><span class="sxs-lookup"><span data-stu-id="e6932-143">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="e6932-144">private</span><span class="sxs-lookup"><span data-stu-id="e6932-144">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="e6932-145">protected</span><span class="sxs-lookup"><span data-stu-id="e6932-145">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="e6932-146">internal</span><span class="sxs-lookup"><span data-stu-id="e6932-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
