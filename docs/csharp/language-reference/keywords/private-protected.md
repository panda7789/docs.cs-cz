---
title: "privátní chráněné (referenční dokumentace jazyka C#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="fb8d8-102">privátní chráněné (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fb8d8-102">private protected (C# Reference)</span></span>
<span data-ttu-id="fb8d8-103">`private protected` – Kombinace klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="fb8d8-104">Privátní chráněného člena je přístupný pro typy odvozené od obsahující třídy, ale pouze v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="fb8d8-105">Porovnání `private protected` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fb8d8-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="fb8d8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb8d8-106">Example</span></span>  
 <span data-ttu-id="fb8d8-107">Privátní chráněného člena základní třídy je přístupná ze odvozené typy v jeho obsahující sestavení, pouze je-li statické typ proměnné typu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-107">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="fb8d8-108">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="fb8d8-108">For example, consider the following code segment:</span></span>  
  
 ```
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
  
```  
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
 <span data-ttu-id="fb8d8-109">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-109">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="fb8d8-110">První soubor obsahuje veřejný základní třídu, `BaseClass`a typ odvozený z něj `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-110">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="fb8d8-111">`BaseClass`vlastní privátní chráněného člena `myValue`, které `DerivedClass1` pokusí o přístup k dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-111">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="fb8d8-112">První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-112">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="fb8d8-113">Ale pokus můžete použít jako zděděného členu v `DerivedClass1` bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-113">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="fb8d8-114">V souboru druhý pokus o přístup `myValue` jako zděděné členem `DerivedClass2` způsobí chybu, protože se jedná pouze přístupný pro odvozené typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-114">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="fb8d8-115">Struktura členové nemohou být `private protected` protože struct nemůže být zděděno.</span><span class="sxs-lookup"><span data-stu-id="fb8d8-115">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fb8d8-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb8d8-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb8d8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb8d8-117">See Also</span></span>  
 <span data-ttu-id="fb8d8-118">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fb8d8-119">[Průvodce programováním v C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="fb8d8-120">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="fb8d8-121">[Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="fb8d8-122">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="fb8d8-123">[Modifikátory](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="fb8d8-124">[veřejné](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="fb8d8-125">[privátní](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="fb8d8-126">[interní](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="fb8d8-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="fb8d8-127">[Otázky zabezpečení pro interní virtuální klíčová slova](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="fb8d8-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
