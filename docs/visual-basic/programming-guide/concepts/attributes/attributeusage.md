---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: dbfbfaa6124eacfd9e4043eab9e4769103e554ca
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524313"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)

Určuje, jak lze použít třídu vlastního atributu. `AttributeUsage` je atribut, který lze použít na definice vlastních atributů pro řízení, jak lze použít nový atribut. Výchozí nastavení vypadají jako v případě explicitního použití:

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

V tomto příkladu lze třídu `NewAttribute` použít na libovolnou entitu kódu s atributem, ale lze ji použít pouze jednou pro každou entitu. Je zděděna odvozenými třídami při použití na základní třídu.

Argumenty `AllowMultiple` a `Inherited` jsou volitelné, takže tento kód má stejný účinek:

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

První argument `AttributeUsage` musí být jeden nebo více prvků výčtu <xref:System.AttributeTargets>. Více cílových typů lze propojit společně s operátorem OR, jako je:

```vb
Imports System
```

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

Pokud je argument `AllowMultiple` nastaven na hodnotu `true`, výsledný atribut lze použít více než jednou pro jednu entitu, například takto:

```vb
Imports System
```

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

V tomto případě se `MultiUseAttr` dá použít opakovaně, protože `AllowMultiple` je nastavená na `true`. Oba formáty zobrazené pro použití více atributů jsou platné.

Pokud je `Inherited` nastavené na `false`, pak atribut nedědí třídy, které jsou odvozeny z třídy s atributem. Příklad:

```vb
Imports System
```

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

V tomto případě se `Attr1` neaplikuje na `DClass` prostřednictvím dědičnosti.

## <a name="remarks"></a>Poznámky

Atribut `AttributeUsage` je atributem jednotného použití--nelze jej použít více než jednou pro stejnou třídu. `AttributeUsage` je alias pro <xref:System.AttributeUsageAttribute>.

Další informace naleznete v tématu [přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Příklad

Následující příklad demonstruje účinek `Inherited` a `AllowMultiple` argumentů atributu `AttributeUsage` a způsob, jakým lze vytvořit výčet vlastních atributů u třídy.

```vb
Imports System
```

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a>Vzorový výstup

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a>Viz také:

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
