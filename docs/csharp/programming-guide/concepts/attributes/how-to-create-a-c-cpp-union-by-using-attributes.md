---
title: Postup vytvoření sjednocení jazyka C/C++ pomocí atributů (C#)
description: Naučte se používat atributy k přizpůsobení způsobu, jakým jsou struktury rozloženy v paměti v jazyce C#. Tento příklad implementuje ekvivalent sjednocení z C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925069"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="268e0-104">Postup vytvoření sjednocení jazyka C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="268e0-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="268e0-105">Pomocí atributů můžete přizpůsobit, jak jsou struktury rozloženy v paměti.</span><span class="sxs-lookup"><span data-stu-id="268e0-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="268e0-106">Můžete například vytvořit, co je v C/C++ známé jako sjednocení pomocí `StructLayout(LayoutKind.Explicit)` `FieldOffset` atributů a.</span><span class="sxs-lookup"><span data-stu-id="268e0-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="268e0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="268e0-107">Example</span></span>

<span data-ttu-id="268e0-108">V tomto segmentu kódu všechna pole `TestUnion` začínají ve stejném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="268e0-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="268e0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="268e0-109">Example</span></span>

<span data-ttu-id="268e0-110">Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.</span><span class="sxs-lookup"><span data-stu-id="268e0-110">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="268e0-111">Dvě celočíselná pole `i1` a `i2` sdílejí stejná umístění v paměti jako `lg` .</span><span class="sxs-lookup"><span data-stu-id="268e0-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="268e0-112">Tento druh řízení nad rozložením struktury je užitečný při volání platformy.</span><span class="sxs-lookup"><span data-stu-id="268e0-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="268e0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="268e0-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="268e0-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="268e0-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="268e0-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="268e0-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="268e0-116">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="268e0-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="268e0-117">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="268e0-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="268e0-118">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="268e0-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="268e0-119">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="268e0-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
