---
title: chráněné vnitřní (C# Reference)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244855"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="2fcf3-102">chráněné vnitřní (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="2fcf3-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="2fcf3-103">`protected internal` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2fcf3-104">Chráněné vnitřní člen je přístupný z aktuálního sestavení nebo typy, které jsou odvozeny ze třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="2fcf3-105">Porovnání `protected internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2fcf3-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="2fcf3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fcf3-106">Example</span></span>  
 <span data-ttu-id="2fcf3-107">Chráněné vnitřní člena základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="2fcf3-108">Je také dostupná v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístup prostřednictvím proměnné typu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="2fcf3-109">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="2fcf3-109">For example, consider the following code segment:</span></span>  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```csharp  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="2fcf3-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="2fcf3-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a jiné třídy `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="2fcf3-112">`BaseClass` vlastní chráněný interní člen `myValue`, který přistupuje `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="2fcf3-113">V souboru druhý pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě při přístupu do tohoto člena prostřednictvím instance třídy odvozená `DerivedClass` proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="2fcf3-114">Členy struktury nemůžou být `protected internal` protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="2fcf3-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2fcf3-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fcf3-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2fcf3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fcf3-116">See Also</span></span>  
 <span data-ttu-id="2fcf3-117">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2fcf3-118">[Průvodce programováním v C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2fcf3-119">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="2fcf3-120">[Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="2fcf3-121">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="2fcf3-122">[Modifikátory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="2fcf3-123">[Veřejné](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="2fcf3-124">[Privátní](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="2fcf3-125">[Interní](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="2fcf3-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="2fcf3-126">[Zajištění zabezpečení pro klíčových slov internal virtual](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="2fcf3-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
