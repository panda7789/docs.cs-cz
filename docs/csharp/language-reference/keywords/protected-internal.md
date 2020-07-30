---
title: Protected Internal-C# – referenční informace
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: 4067da93bcceba0fa3e4a14aa58b4cde812412f3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301785"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="d9206-102">Protected Internal (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d9206-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="d9206-103">`protected internal`Kombinace klíčového slova je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="d9206-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="d9206-104">Chráněný interní člen je přístupný z aktuálního sestavení nebo z typů, které jsou odvozeny z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="d9206-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="d9206-105">Porovnání `protected internal` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d9206-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="d9206-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9206-106">Example</span></span>

<span data-ttu-id="d9206-107">Chráněný interní člen základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9206-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="d9206-108">Je také přístupný v odvozené třídě nacházející se v jiném sestavení pouze v případě, že k přístupu dojde prostřednictvím proměnné odvozeného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="d9206-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="d9206-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="d9206-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="d9206-110">Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="d9206-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="d9206-111">První soubor obsahuje veřejnou základní třídu, `BaseClass` a další třídu, `TestAccess` .</span><span class="sxs-lookup"><span data-stu-id="d9206-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="d9206-112">`BaseClass`vlastní chráněný interní člen, `myValue` , který je k dispozici pro daný `TestAccess` typ.</span><span class="sxs-lookup"><span data-stu-id="d9206-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="d9206-113">Ve druhém souboru dojde k pokusu o přístup `myValue` prostřednictvím instance aplikace k `BaseClass` chybě, zatímco přístup k tomuto členu prostřednictvím instance odvozené třídy `DerivedClass` bude úspěšný.</span><span class="sxs-lookup"><span data-stu-id="d9206-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="d9206-114">Členy struktury nemůžou být `protected internal` zděděné, protože strukturu nejde zdědit.</span><span class="sxs-lookup"><span data-stu-id="d9206-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9206-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9206-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d9206-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9206-116">See also</span></span>

- [<span data-ttu-id="d9206-117">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9206-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9206-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d9206-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9206-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9206-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d9206-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="d9206-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="d9206-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="d9206-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="d9206-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="d9206-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d9206-123">public</span><span class="sxs-lookup"><span data-stu-id="d9206-123">public</span></span>](public.md)
- [<span data-ttu-id="d9206-124">hlášen</span><span class="sxs-lookup"><span data-stu-id="d9206-124">private</span></span>](private.md)
- [<span data-ttu-id="d9206-125">internal</span><span class="sxs-lookup"><span data-stu-id="d9206-125">internal</span></span>](internal.md)
- <span data-ttu-id="d9206-126">[Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d9206-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
