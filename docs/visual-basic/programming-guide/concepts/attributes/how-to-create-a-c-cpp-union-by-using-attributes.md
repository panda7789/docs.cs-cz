---
title: 'Postupy: vytváření sjednocení C-C++ pomocí atributů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: b07168df3fb7ec8195a3f64ef5b1bef0cc16dda2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)
Pomocí atributů můžete přizpůsobit, jak jsou rozloženy struktury v paměti. Například můžete vytvořit, která se označuje jako sjednocení v jazyce C/C++ pomocí `StructLayout(LayoutKind.Explicit)` a `FieldOffset` atributy.  
  
## <a name="example"></a>Příklad  
 V tomto segmentu kódu, všechna pole z `TestUnion` spustit ve stejném umístění v paměti.  
  
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
 Zde je další příklad kde počáteční pole v různých explicitně nastavit umístění.  
  
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
  
 Pole dva celé číslo `i1` a `i2`, sdílet stejné umístění paměti jako `lg`. Tento druh kontrolu nad struktura rozložení je užitečné při použití vyvolání platformy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atributy](../../../../standard/attributes/index.md)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
