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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Jak vytvořit sjednocení C/C++ pomocí atributů (C#)

Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti. Můžete například vytvořit to, co je známé jako unie v `StructLayout(LayoutKind.Explicit)` `FieldOffset` jazyce C/C++ pomocí atributů a.

## <a name="example"></a>Příklad

V tomto segmentu kódu všechna `TestUnion` pole začít ve stejném umístění v paměti.

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

Následuje další příklad, kde pole začínají v různých explicitně nastavených umístěních.

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

Dvě celá pole `i1` a `i2`, sdílejí stejná `lg`umístění paměti jako . Tento druh kontroly nad rozložení struktury je užitečné při použití vyvolání platformy.

## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Programovací příručka jazyka C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](index.md)
- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
