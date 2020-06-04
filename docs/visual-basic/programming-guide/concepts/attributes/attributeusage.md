---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400729"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)

Určuje, jak lze použít třídu vlastního atributu. `AttributeUsage`je atribut, který lze použít na definice vlastních atributů pro řízení, jak lze použít nový atribut. Výchozí nastavení vypadají jako v případě explicitního použití:

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

V tomto příkladu `NewAttribute` lze třídu použít pro libovolnou entitu kódu s atributem, ale lze ji použít pouze jednou pro každou entitu. Je zděděna odvozenými třídami při použití na základní třídu.

`AllowMultiple`Argumenty a `Inherited` jsou volitelné, takže tento kód má stejný účinek:

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

První `AttributeUsage` argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu. Více cílových typů lze propojit společně s operátorem OR, jako je:

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

Pokud `AllowMultiple` je argument nastaven na `true` , pak výsledný atribut lze použít více než jednou pro jednu entitu, například takto:

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

V tomto případě `MultiUseAttr` je možné provést opakované použití, protože `AllowMultiple` je nastavena na `true` . Oba formáty zobrazené pro použití více atributů jsou platné.

Pokud `Inherited` je nastaven na `false` , pak atribut není zděděn třídami, které jsou odvozeny z třídy s atributem. Příklad:

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

V tomto případě `Attr1` se nepoužije na `DClass` dědění.

## <a name="remarks"></a>Poznámky

`AttributeUsage`Atribut je atribut s jedním použitím – nelze jej použít více než jednou pro stejnou třídu. `AttributeUsage`je alias pro <xref:System.AttributeUsageAttribute> .

Další informace naleznete v tématu [přístup k atributům pomocí reflexe (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje účinek `Inherited` `AllowMultiple` argumentů a pro `AttributeUsage` atribut a způsob, jakým lze vytvořit výčet vlastních atributů pro třídu.

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

## <a name="see-also"></a>Viz také

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Příručka k programování v jazyce Visual Basic](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../reflection.md)
- [Atributy (Visual Basic)](../../../language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](accessing-attributes-by-using-reflection.md)
