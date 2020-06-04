---
title: 'Postupy: vytvoření sjednocení jazyka C-C pomocí atributů'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400678"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)

Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti. Můžete například vytvořit, co je v C/C++ známé jako sjednocení pomocí `StructLayout(LayoutKind.Explicit)` `FieldOffset` atributů a.

## <a name="example"></a>Příklad

V tomto segmentu kódu všechna pole `TestUnion` začínají ve stejném umístění v paměti.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>Příklad

Následuje další příklad, kdy se pole spouštějí v různých explicitních nastaveních umístění.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

Dvě celočíselná pole `i1` a `i2` sdílejí stejná umístění v paměti jako `lg` . Tento druh řízení nad rozložením struktury je užitečný při volání platformy.

## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Příručka k programování v jazyce Visual Basic](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../reflection.md)
- [Atributy (Visual Basic)](../../../language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](accessing-attributes-by-using-reflection.md)
