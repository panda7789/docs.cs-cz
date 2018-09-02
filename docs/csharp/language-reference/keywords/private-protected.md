---
title: Private protected (referenční dokumentace jazyka C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 4a4ee999fe932674e854b1428ab33b33bc71d2ad
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419531"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="dfbbb-102">Private protected (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dfbbb-102">private protected (C# Reference)</span></span>

<span data-ttu-id="dfbbb-103">`private protected` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="dfbbb-104">Privátní chráněný člen je přístupný pro typy odvozené od obsahující třídy, ale pouze v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="dfbbb-105">Porovnání `private protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dfbbb-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="dfbbb-106">`private protected` Modifikátor přístupu je platný v jazyce C# verze 7.2 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="dfbbb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfbbb-107">Example</span></span>

<span data-ttu-id="dfbbb-108">Privátní chráněného člena základní třídy je přístupný z odvozených typů v sestavení obsahující pouze v případě, statický typ proměnné je typ odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="dfbbb-109">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="dfbbb-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="dfbbb-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="dfbbb-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a typ odvozený z ní, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="dfbbb-112">`BaseClass` vlastní privátní chráněný člen `myValue`, což `DerivedClass1` pokusí o přístup k dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="dfbbb-113">První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="dfbbb-114">Nicméně pokus o jeho použití jako zděděného člena v `DerivedClass1` proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="dfbbb-115">V souboru druhý pokus o přístup k `myValue` jako zděděný člen `DerivedClass2` dojde k chybě, protože byl přístupný pouze odvozenými typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="dfbbb-116">Členy struktury nemůžou být `private protected` protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="dfbbb-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="dfbbb-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfbbb-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="dfbbb-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfbbb-118">See also</span></span>

- [<span data-ttu-id="dfbbb-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfbbb-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfbbb-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfbbb-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfbbb-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfbbb-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dfbbb-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="dfbbb-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="dfbbb-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="dfbbb-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="dfbbb-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="dfbbb-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="dfbbb-125">public</span><span class="sxs-lookup"><span data-stu-id="dfbbb-125">public</span></span>](public.md)
- [<span data-ttu-id="dfbbb-126">private</span><span class="sxs-lookup"><span data-stu-id="dfbbb-126">private</span></span>](private.md)
- [<span data-ttu-id="dfbbb-127">internal</span><span class="sxs-lookup"><span data-stu-id="dfbbb-127">internal</span></span>](internal.md)
- <span data-ttu-id="dfbbb-128">[Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfbbb-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>