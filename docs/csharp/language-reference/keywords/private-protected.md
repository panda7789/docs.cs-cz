---
title: Private protected (referenční dokumentace jazyka C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961129"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="e7f7f-102">Private protected (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e7f7f-102">private protected (C# Reference)</span></span>
<span data-ttu-id="e7f7f-103">`private protected` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e7f7f-104">Privátní chráněný člen je přístupný pro typy odvozené od obsahující třídy, ale pouze v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="e7f7f-105">Porovnání `private protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e7f7f-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="e7f7f-106">`private protected` Modifikátor přístupu je platný v jazyce C# verze 7.2 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>
   
## <a name="example"></a><span data-ttu-id="e7f7f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7f7f-107">Example</span></span>  
 <span data-ttu-id="e7f7f-108">Privátní chráněného člena základní třídy je přístupný z odvozených typů v sestavení obsahující pouze v případě, statický typ proměnné je typ odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="e7f7f-109">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="e7f7f-109">For example, consider the following code segment:</span></span>  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="e7f7f-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="e7f7f-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a typ odvozený z ní, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="e7f7f-112">`BaseClass` vlastní privátní chráněný člen `myValue`, což `DerivedClass1` pokusí o přístup k dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="e7f7f-113">První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="e7f7f-114">Nicméně pokus o jeho použití jako zděděného člena v `DerivedClass1` proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="e7f7f-115">V souboru druhý pokus o přístup k `myValue` jako zděděný člen `DerivedClass2` dojde k chybě, protože byl přístupný pouze odvozenými typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="e7f7f-116">Členy struktury nemůžou být `private protected` protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="e7f7f-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e7f7f-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e7f7f-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7f7f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7f7f-118">See Also</span></span>  
 <span data-ttu-id="e7f7f-119">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e7f7f-120">[Průvodce programováním v C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e7f7f-121">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-121">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e7f7f-122">[Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-122">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="e7f7f-123">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-123">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="e7f7f-124">[Modifikátory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-124">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="e7f7f-125">[Veřejné](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-125">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="e7f7f-126">[Privátní](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-126">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="e7f7f-127">[Interní](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="e7f7f-127">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="e7f7f-128">[Zajištění zabezpečení pro klíčových slov internal virtual](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="e7f7f-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
