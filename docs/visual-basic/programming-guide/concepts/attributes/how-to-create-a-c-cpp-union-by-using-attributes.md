---
title: 'Postupy: vytvořeníC++ sjednocení jazyka C pomocí atributů'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: acb8dc781e2872ae46e5aa058a98b3dd98f3e064
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349502"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Postupy: vytvoření C/C++ sjednocení pomocí atributů (Visual Basic)

Pomocí atributů můžete přizpůsobit způsob, jakým jsou struktury rozloženy v paměti. Můžete například vytvořit, co se říká sjednocení v C/C++ pomocí atributů `StructLayout(LayoutKind.Explicit)` a `FieldOffset`.

## <a name="example"></a>Příklad

V tomto segmentu kódu se všechna pole `TestUnion` začínají na stejném místě v paměti.

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

Dvě celočíselná pole, `i1` a `i2`, sdílejí stejná umístění v paměti jako `lg`. Tento druh řízení nad rozložením struktury je užitečný při volání platformy.

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
