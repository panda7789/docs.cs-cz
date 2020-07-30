---
title: Private Protected – reference jazyka C#
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: 94ef55d7e13841f81b036f52659b215e22a3a0d7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301798"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="dfc61-102">Private Protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dfc61-102">private protected (C# Reference)</span></span>

<span data-ttu-id="dfc61-103">`private protected`Kombinace klíčového slova je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="dfc61-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="dfc61-104">Soukromý chráněný člen je přístupný z typů odvozených z obsahující třídy, ale pouze v rámci nadřazeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfc61-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="dfc61-105">Porovnání `private protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dfc61-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="dfc61-106">`private protected`Modifikátor přístupu je platný v jazyce C# verze 7,2 a novějším.</span><span class="sxs-lookup"><span data-stu-id="dfc61-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="dfc61-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfc61-107">Example</span></span>

<span data-ttu-id="dfc61-108">Soukromý chráněný člen základní třídy je přístupný z odvozených typů v jeho obsahujícím sestavení pouze v případě, že statický typ proměnné je odvozený typ třídy.</span><span class="sxs-lookup"><span data-stu-id="dfc61-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="dfc61-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="dfc61-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="dfc61-110">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="dfc61-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="dfc61-111">První soubor obsahuje veřejnou základní třídu, `BaseClass` a typ, který je z něj odvozený `DerivedClass1` .</span><span class="sxs-lookup"><span data-stu-id="dfc61-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="dfc61-112">`BaseClass`vlastní soukromý chráněný člen, `myValue` , který se `DerivedClass1` snaží získat přístup dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="dfc61-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="dfc61-113">Při prvním pokusu o přístup `myValue` prostřednictvím instance `BaseClass` se vytvoří chyba.</span><span class="sxs-lookup"><span data-stu-id="dfc61-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="dfc61-114">Pokus o jeho použití jako zděděný člen v nástroji bude ale `DerivedClass1` úspěšný.</span><span class="sxs-lookup"><span data-stu-id="dfc61-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="dfc61-115">Ve druhém souboru dojde k chybě pokusu o přístup `myValue` jako zděděný člen `DerivedClass2` , protože je přístupný pouze pro odvozené typy v Assembly1.</span><span class="sxs-lookup"><span data-stu-id="dfc61-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="dfc61-116">Pokud `Assembly1.cs` obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> název `Assembly2` , odvozená třída `DerivedClass1` bude mít přístup ke `private protected` členům deklarovaným v `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="dfc61-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="dfc61-117">`InternalsVisibleTo`zpřístupňuje `private protected` členy na odvozených třídách v jiných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="dfc61-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="dfc61-118">Členy struktury nemůžou být `private protected` zděděné, protože strukturu nejde zdědit.</span><span class="sxs-lookup"><span data-stu-id="dfc61-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dfc61-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfc61-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dfc61-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfc61-120">See also</span></span>

- [<span data-ttu-id="dfc61-121">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfc61-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfc61-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dfc61-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfc61-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfc61-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dfc61-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="dfc61-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="dfc61-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="dfc61-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="dfc61-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="dfc61-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="dfc61-127">public</span><span class="sxs-lookup"><span data-stu-id="dfc61-127">public</span></span>](public.md)
- [<span data-ttu-id="dfc61-128">hlášen</span><span class="sxs-lookup"><span data-stu-id="dfc61-128">private</span></span>](private.md)
- [<span data-ttu-id="dfc61-129">internal</span><span class="sxs-lookup"><span data-stu-id="dfc61-129">internal</span></span>](internal.md)
- <span data-ttu-id="dfc61-130">[Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfc61-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
