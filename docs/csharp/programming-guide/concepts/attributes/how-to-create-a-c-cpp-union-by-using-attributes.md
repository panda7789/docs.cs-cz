---
title: Postup vytvoření C/C++ sjednocení pomocí atributů ()C#
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141570"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="4b513-102">Postup vytvoření C/C++ sjednocení pomocí atributů ()C#</span><span class="sxs-lookup"><span data-stu-id="4b513-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="4b513-103">Pomocí atributů můžete přizpůsobit, jak jsou struktury rozloženy v paměti.</span><span class="sxs-lookup"><span data-stu-id="4b513-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="4b513-104">Můžete například vytvořit, co se říká sjednocení v C/C++ pomocí atributů `StructLayout(LayoutKind.Explicit)` a `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="4b513-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="4b513-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b513-105">Example</span></span>

<span data-ttu-id="4b513-106">V tomto segmentu kódu se všechna pole `TestUnion` začínají na stejném místě v paměti.</span><span class="sxs-lookup"><span data-stu-id="4b513-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="4b513-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b513-107">Example</span></span>

<span data-ttu-id="4b513-108">Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.</span><span class="sxs-lookup"><span data-stu-id="4b513-108">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="4b513-109">Dvě celočíselná pole, `i1` a `i2`, sdílejí stejná umístění v paměti jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="4b513-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="4b513-110">Tento druh řízení nad rozložením struktury je užitečný při volání platformy.</span><span class="sxs-lookup"><span data-stu-id="4b513-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b513-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b513-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="4b513-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4b513-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="4b513-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b513-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="4b513-114">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="4b513-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="4b513-115">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="4b513-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="4b513-116">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="4b513-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="4b513-117">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="4b513-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
