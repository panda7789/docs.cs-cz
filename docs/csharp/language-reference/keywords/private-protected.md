---
title: soukromý chráněný – C# odkaz
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713206"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="a88bb-102">Private ProtectedC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="a88bb-102">private protected (C# Reference)</span></span>

<span data-ttu-id="a88bb-103">Kombinací klíčového slova `private protected` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="a88bb-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a88bb-104">Soukromý chráněný člen je přístupný z typů odvozených z obsahující třídy, ale pouze v rámci nadřazeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a88bb-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="a88bb-105">Porovnání `private protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a88bb-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a88bb-106">Modifikátor přístupu `private protected` je platný ve C# verzi 7,2 a novější.</span><span class="sxs-lookup"><span data-stu-id="a88bb-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="a88bb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a88bb-107">Example</span></span>

<span data-ttu-id="a88bb-108">Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahujícím sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy.</span><span class="sxs-lookup"><span data-stu-id="a88bb-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="a88bb-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="a88bb-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="a88bb-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="a88bb-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="a88bb-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a typ odvozený z něj, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="a88bb-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="a88bb-112">`BaseClass` vlastní soukromý chráněný člen, `myValue`, který `DerivedClass1` se snaží získat přístup dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="a88bb-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="a88bb-113">První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` vytvoří chybu.</span><span class="sxs-lookup"><span data-stu-id="a88bb-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="a88bb-114">Ale pokus o použití jako zděděného člena v `DerivedClass1` úspěšný bude.</span><span class="sxs-lookup"><span data-stu-id="a88bb-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="a88bb-115">Ve druhém souboru se pokus o přístup k `myValue` jako zděděný člen `DerivedClass2` vytvoří chyba, protože je přístupná pouze pro odvozené typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="a88bb-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="a88bb-116">Členy struktury nelze `private protected`, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="a88bb-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="a88bb-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a88bb-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="a88bb-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a88bb-118">See also</span></span>

- [<span data-ttu-id="a88bb-119">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="a88bb-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a88bb-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a88bb-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a88bb-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a88bb-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a88bb-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a88bb-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a88bb-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="a88bb-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a88bb-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="a88bb-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a88bb-125">public</span><span class="sxs-lookup"><span data-stu-id="a88bb-125">public</span></span>](public.md)
- [<span data-ttu-id="a88bb-126">private</span><span class="sxs-lookup"><span data-stu-id="a88bb-126">private</span></span>](private.md)
- [<span data-ttu-id="a88bb-127">internal</span><span class="sxs-lookup"><span data-stu-id="a88bb-127">internal</span></span>](internal.md)
- <span data-ttu-id="a88bb-128">[Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a88bb-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
