---
title: chráněná interní C# reference
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 6e5a4c6e63c2c05df54df6bed542eab3f43f9272
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422575"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="306d1-102">chráněný interní (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="306d1-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="306d1-103">Kombinací klíčového slova `protected internal` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="306d1-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="306d1-104">Chráněný interní člen je přístupný z aktuálního sestavení nebo z typů, které jsou odvozeny z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="306d1-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="306d1-105">Porovnání `protected internal` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="306d1-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="306d1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="306d1-106">Example</span></span>

<span data-ttu-id="306d1-107">Chráněný interní člen základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="306d1-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="306d1-108">Je také přístupný v odvozené třídě nacházející se v jiném sestavení pouze v případě, že k přístupu dojde prostřednictvím proměnné odvozeného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="306d1-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="306d1-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="306d1-109">For example, consider the following code segment:</span></span>

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
        var baseObject = new BaseClass();
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
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="306d1-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="306d1-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="306d1-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a jinou třídu `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="306d1-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="306d1-112">`BaseClass` vlastní chráněný interní člen, `myValue`, ke kterému se přistupoval pomocí typu `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="306d1-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="306d1-113">V druhém souboru dojde k pokusu o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě, zatímco přístup k tomuto členu prostřednictvím instance odvozené třídy, `DerivedClass` bude úspěšný.</span><span class="sxs-lookup"><span data-stu-id="306d1-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="306d1-114">Členy struktury nelze `protected internal`, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="306d1-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="306d1-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="306d1-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="306d1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="306d1-116">See also</span></span>

- [<span data-ttu-id="306d1-117">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="306d1-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="306d1-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="306d1-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="306d1-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="306d1-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="306d1-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="306d1-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="306d1-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="306d1-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="306d1-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="306d1-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="306d1-123">public</span><span class="sxs-lookup"><span data-stu-id="306d1-123">public</span></span>](public.md)
- [<span data-ttu-id="306d1-124">private</span><span class="sxs-lookup"><span data-stu-id="306d1-124">private</span></span>](private.md)
- [<span data-ttu-id="306d1-125">internal</span><span class="sxs-lookup"><span data-stu-id="306d1-125">internal</span></span>](internal.md)
- <span data-ttu-id="306d1-126">[Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="306d1-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
