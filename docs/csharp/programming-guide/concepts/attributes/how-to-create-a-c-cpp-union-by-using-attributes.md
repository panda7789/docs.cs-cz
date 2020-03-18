---
title: Jak vytvořit sjednocení C/C++ pomocí atributů (C#)
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141570"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="a9a3c-102">Jak vytvořit sjednocení C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="a9a3c-103">Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="a9a3c-104">Můžete například vytvořit to, co je známé jako unie v `StructLayout(LayoutKind.Explicit)` `FieldOffset` jazyce C/C++ pomocí atributů a.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="a9a3c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9a3c-105">Example</span></span>

<span data-ttu-id="a9a3c-106">V tomto segmentu kódu všechna `TestUnion` pole začít ve stejném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="a9a3c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9a3c-107">Example</span></span>

<span data-ttu-id="a9a3c-108">Následuje další příklad, kde pole začínají v různých explicitně nastavených umístěních.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="a9a3c-109">Dvě celá pole `i1` a `i2`, sdílejí stejná `lg`umístění paměti jako .</span><span class="sxs-lookup"><span data-stu-id="a9a3c-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="a9a3c-110">Tento druh kontroly nad rozložení struktury je užitečné při použití vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="a9a3c-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a3c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9a3c-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="a9a3c-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9a3c-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a9a3c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9a3c-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="a9a3c-114">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a9a3c-115">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="a9a3c-116">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="a9a3c-117">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="a9a3c-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
