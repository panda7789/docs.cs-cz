---
title: privátní chráněné - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463045"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="1b034-102">privátní chráněné (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="1b034-102">private protected (C# Reference)</span></span>

<span data-ttu-id="1b034-103">Kombinace `private protected` klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="1b034-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="1b034-104">Soukromý chráněný člen je přístupný typy odvozené z obsahující třídy, ale pouze v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="1b034-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="1b034-105">Porovnání `private protected` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b034-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1b034-106">Modifikátor `private protected` přístupu je platný v c# verze 7.2 a novější.</span><span class="sxs-lookup"><span data-stu-id="1b034-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="1b034-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b034-107">Example</span></span>

<span data-ttu-id="1b034-108">Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahující sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy.</span><span class="sxs-lookup"><span data-stu-id="1b034-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="1b034-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="1b034-109">For example, consider the following code segment:</span></span>

```csharp
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

<span data-ttu-id="1b034-110">Tento příklad obsahuje `Assembly1.cs` dva `Assembly2.cs`soubory a .</span><span class="sxs-lookup"><span data-stu-id="1b034-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="1b034-111">První soubor obsahuje třídu `BaseClass`public base a typ z `DerivedClass1`něj odvozený .</span><span class="sxs-lookup"><span data-stu-id="1b034-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="1b034-112">`BaseClass`vlastní soukromý chráněný člen `myValue`, `DerivedClass1` který se pokusí o přístup dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="1b034-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="1b034-113">První pokus o `myValue` přístup prostřednictvím instance `BaseClass` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="1b034-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="1b034-114">Pokus o jeho použití jako zděděného člena v aplikaci však `DerivedClass1` bude úspěšný.</span><span class="sxs-lookup"><span data-stu-id="1b034-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="1b034-115">V druhém souboru pokus `myValue` o přístup jako `DerivedClass2` zděděný člen způsobí chybu, protože je přístupný pouze odvozené typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="1b034-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="1b034-116">Pokud `Assembly1.cs` obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> tento `Assembly2`název , `DerivedClass1` odvozené třídy bude mít přístup k členům `private protected` deklarované v `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="1b034-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="1b034-117">`InternalsVisibleTo`zviditelní `private protected` členy odvozených tříd v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="1b034-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="1b034-118">Členy struktury nelze `private protected` zdědit, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="1b034-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1b034-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b034-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1b034-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b034-120">See also</span></span>

- [<span data-ttu-id="1b034-121">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b034-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b034-122">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b034-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1b034-123">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1b034-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1b034-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="1b034-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="1b034-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="1b034-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="1b034-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1b034-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1b034-127">public</span><span class="sxs-lookup"><span data-stu-id="1b034-127">public</span></span>](public.md)
- [<span data-ttu-id="1b034-128">private</span><span class="sxs-lookup"><span data-stu-id="1b034-128">private</span></span>](private.md)
- [<span data-ttu-id="1b034-129">internal</span><span class="sxs-lookup"><span data-stu-id="1b034-129">internal</span></span>](internal.md)
- <span data-ttu-id="1b034-130">[Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b034-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
