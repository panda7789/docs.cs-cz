---
title: chráněné vnitřní (C# Reference)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 1a305cb84989f12350e2e7cc28dd18f9d0c7ae5e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536408"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="a87f2-102">chráněné vnitřní (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="a87f2-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="a87f2-103">`protected internal` – Kombinace klíčových slov je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="a87f2-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a87f2-104">Chráněné vnitřní člen je přístupný z aktuálního sestavení nebo typy, které jsou odvozeny ze třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="a87f2-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="a87f2-105">Porovnání `protected internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a87f2-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="a87f2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a87f2-106">Example</span></span>

<span data-ttu-id="a87f2-107">Chráněné vnitřní člena základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="a87f2-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="a87f2-108">Je také dostupná v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístup prostřednictvím proměnné typu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="a87f2-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="a87f2-109">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="a87f2-109">For example, consider the following code segment:</span></span>

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
        BaseClass baseObject = new BaseClass();
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
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```
<span data-ttu-id="a87f2-110">Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="a87f2-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="a87f2-111">První soubor obsahuje veřejnou základní třídu, `BaseClass`a jiné třídy `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="a87f2-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="a87f2-112">`BaseClass` vlastní chráněný interní člen `myValue`, který přistupuje `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="a87f2-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="a87f2-113">V souboru druhý pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě při přístupu do tohoto člena prostřednictvím instance třídy odvozená `DerivedClass` proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="a87f2-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="a87f2-114">Členy struktury nemůžou být `protected internal` protože struktury nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="a87f2-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a87f2-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a87f2-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a87f2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a87f2-116">See also</span></span>

- [<span data-ttu-id="a87f2-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a87f2-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a87f2-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a87f2-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a87f2-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a87f2-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a87f2-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a87f2-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a87f2-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="a87f2-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a87f2-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="a87f2-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="a87f2-123">public</span><span class="sxs-lookup"><span data-stu-id="a87f2-123">public</span></span>](public.md)
- [<span data-ttu-id="a87f2-124">private</span><span class="sxs-lookup"><span data-stu-id="a87f2-124">private</span></span>](private.md)
- [<span data-ttu-id="a87f2-125">internal</span><span class="sxs-lookup"><span data-stu-id="a87f2-125">internal</span></span>](internal.md)
- <span data-ttu-id="a87f2-126">[Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a87f2-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>