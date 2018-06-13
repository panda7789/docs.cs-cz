---
title: chráněné vnitřní (C# referenční dokumentace)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172238"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="b97f2-102">chráněné vnitřní (C# referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="b97f2-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="b97f2-103">`protected internal` – Kombinace klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="b97f2-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="b97f2-104">Chráněný člen interní je přístupný z aktuální sestavení nebo z typů, které jsou odvozeny od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="b97f2-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="b97f2-105">Porovnání `protected internal` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b97f2-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="b97f2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b97f2-106">Example</span></span>  
 <span data-ttu-id="b97f2-107">Chráněný vnitřní člen základní třídy je přístupná z libovolného typu v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b97f2-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="b97f2-108">Je také přístupné v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístupu pomocí proměnné typu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b97f2-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="b97f2-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="b97f2-109">For example, consider the following code segment:</span></span>  

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
 <span data-ttu-id="b97f2-110">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="b97f2-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="b97f2-111">První soubor obsahuje veřejný základní třídu, `BaseClass`a jinou třídu, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="b97f2-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="b97f2-112">`BaseClass` vlastní chráněný vnitřní člen, `myValue`, který přistupuje `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="b97f2-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="b97f2-113">V souboru druhý pokus o přístup `myValue` prostřednictvím instance `BaseClass` vygeneruje chybu při přístupu do tohoto člena prostřednictvím instance odvozené třídy, `DerivedClass` bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b97f2-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="b97f2-114">Struktura členové nemohou být `protected internal` protože struct nemůže být zděděno.</span><span class="sxs-lookup"><span data-stu-id="b97f2-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b97f2-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b97f2-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b97f2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b97f2-116">See Also</span></span>  
 <span data-ttu-id="b97f2-117">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b97f2-118">[Průvodce programováním v C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b97f2-119">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b97f2-120">[Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="b97f2-121">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="b97f2-122">[Modifikátory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="b97f2-123">[Veřejné](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="b97f2-124">[Privátní](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="b97f2-125">[Interní](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="b97f2-126">[Otázky zabezpečení pro interní virtuální klíčová slova](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="b97f2-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
