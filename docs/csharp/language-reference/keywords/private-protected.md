---
title: privátní chráněné - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713206"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="3b009-102">privátní chráněné (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="3b009-102">private protected (C# Reference)</span></span>

<span data-ttu-id="3b009-103">Kombinace `private protected` klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="3b009-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="3b009-104">Soukromý chráněný člen je přístupný typy odvozené z obsahující třídy, ale pouze v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b009-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="3b009-105">Porovnání `private protected` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3b009-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b009-106">Modifikátor `private protected` přístupu je platný v c# verze 7.2 a novější.</span><span class="sxs-lookup"><span data-stu-id="3b009-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="3b009-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b009-107">Example</span></span>

<span data-ttu-id="3b009-108">Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahující sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy.</span><span class="sxs-lookup"><span data-stu-id="3b009-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="3b009-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="3b009-109">For example, consider the following code segment:</span></span>  

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
        var baseObject = new BaseClass();

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

<span data-ttu-id="3b009-110">Tento příklad obsahuje `Assembly1.cs` dva `Assembly2.cs`soubory a .</span><span class="sxs-lookup"><span data-stu-id="3b009-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="3b009-111">První soubor obsahuje třídu `BaseClass`public base a typ z `DerivedClass1`něj odvozený .</span><span class="sxs-lookup"><span data-stu-id="3b009-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="3b009-112">`BaseClass`vlastní soukromý chráněný člen `myValue`, `DerivedClass1` který se pokusí o přístup dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="3b009-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="3b009-113">První pokus o `myValue` přístup prostřednictvím instance `BaseClass` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="3b009-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="3b009-114">Pokus o jeho použití jako zděděného člena v aplikaci však `DerivedClass1` bude úspěšný.</span><span class="sxs-lookup"><span data-stu-id="3b009-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="3b009-115">V druhém souboru pokus `myValue` o přístup jako `DerivedClass2` zděděný člen způsobí chybu, protože je přístupný pouze odvozené typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="3b009-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="3b009-116">Členy struktury nelze `private protected` zdědit, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="3b009-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="3b009-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b009-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="3b009-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b009-118">See also</span></span>

- [<span data-ttu-id="3b009-119">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b009-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3b009-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b009-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3b009-121">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3b009-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3b009-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3b009-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3b009-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="3b009-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3b009-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="3b009-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3b009-125">Veřejné</span><span class="sxs-lookup"><span data-stu-id="3b009-125">public</span></span>](public.md)
- [<span data-ttu-id="3b009-126">Soukromé</span><span class="sxs-lookup"><span data-stu-id="3b009-126">private</span></span>](private.md)
- [<span data-ttu-id="3b009-127">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="3b009-127">internal</span></span>](internal.md)
- <span data-ttu-id="3b009-128">[Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3b009-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
