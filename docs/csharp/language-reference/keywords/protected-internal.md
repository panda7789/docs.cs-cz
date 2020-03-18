---
title: chráněné vnitřní - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713193"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="7c334-102">chráněné interní (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="7c334-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="7c334-103">Kombinace `protected internal` klíčových slov je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="7c334-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="7c334-104">Chráněný interní člen je přístupný z aktuálního sestavení nebo z typů, které jsou odvozeny z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="7c334-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="7c334-105">Porovnání `protected internal` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7c334-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c334-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c334-106">Example</span></span>

<span data-ttu-id="7c334-107">Chráněný vnitřní člen základní třídy je přístupný z libovolného typu v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c334-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="7c334-108">Je také přístupný v odvozené třídě umístěné v jiném sestavení pouze v případě, že přístup probíhá prostřednictvím proměnné odvozeného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="7c334-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="7c334-109">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="7c334-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="7c334-110">Tento příklad obsahuje `Assembly1.cs` dva `Assembly2.cs`soubory a .</span><span class="sxs-lookup"><span data-stu-id="7c334-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="7c334-111">První soubor obsahuje třídu `BaseClass`public base a `TestAccess`jinou třídu .</span><span class="sxs-lookup"><span data-stu-id="7c334-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="7c334-112">`BaseClass`vlastní chráněný interní člen `myValue`, ke kterému `TestAccess` má typ přístup.</span><span class="sxs-lookup"><span data-stu-id="7c334-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="7c334-113">V druhém souboru pokus `myValue` o přístup `BaseClass` prostřednictvím instance způsobí chybu, zatímco přístup k tomuto členu prostřednictvím instance odvozené třídy, `DerivedClass` bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="7c334-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="7c334-114">Členy struktury nelze `protected internal` zdědit, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="7c334-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7c334-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7c334-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7c334-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c334-116">See also</span></span>

- [<span data-ttu-id="7c334-117">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7c334-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7c334-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7c334-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7c334-119">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7c334-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7c334-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="7c334-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="7c334-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="7c334-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="7c334-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="7c334-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7c334-123">Veřejné</span><span class="sxs-lookup"><span data-stu-id="7c334-123">public</span></span>](public.md)
- [<span data-ttu-id="7c334-124">Soukromé</span><span class="sxs-lookup"><span data-stu-id="7c334-124">private</span></span>](private.md)
- [<span data-ttu-id="7c334-125">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="7c334-125">internal</span></span>](internal.md)
- <span data-ttu-id="7c334-126">[Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7c334-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
