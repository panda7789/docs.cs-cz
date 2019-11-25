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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Postup vytvoření C/C++ sjednocení pomocí atributů ()C#

Pomocí atributů můžete přizpůsobit, jak jsou struktury rozloženy v paměti. Můžete například vytvořit, co se říká sjednocení v C/C++ pomocí atributů `StructLayout(LayoutKind.Explicit)` a `FieldOffset`.

## <a name="example"></a>Příklad

V tomto segmentu kódu se všechna pole `TestUnion` začínají na stejném místě v paměti.

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

Dvě celočíselná pole, `i1` a `i2`, sdílejí stejná umístění v paměti jako `lg`. Tento druh řízení nad rozložením struktury je užitečný při volání platformy.

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](index.md)
- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
