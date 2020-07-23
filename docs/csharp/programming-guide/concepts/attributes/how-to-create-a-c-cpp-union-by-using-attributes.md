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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Postup vytvoření sjednocení jazyka C/C++ pomocí atributů (C#)

Pomocí atributů můžete přizpůsobit, jak jsou struktury rozloženy v paměti. Můžete například vytvořit, co je v C/C++ známé jako sjednocení pomocí `StructLayout(LayoutKind.Explicit)` `FieldOffset` atributů a.

## <a name="example"></a>Příklad

V tomto segmentu kódu všechna pole `TestUnion` začínají ve stejném umístění v paměti.

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

## <a name="example"></a>Příklad

Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.

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

Dvě celočíselná pole `i1` a `i2` sdílejí stejná umístění v paměti jako `lg` . Tento druh řízení nad rozložením struktury je užitečný při volání platformy.

## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](index.md)
- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
