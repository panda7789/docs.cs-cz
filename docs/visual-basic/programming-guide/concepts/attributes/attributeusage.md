---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 0e88c57b2a18afb7f9f7d567f355d38a78892b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648138"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Určuje, jak je možné třídu vlastního atributu. `AttributeUsage` představuje atribut, který lze použít pro definice vlastní atribut pro řízení použití nového atributu. Výchozí nastavení se při použití explicitně vypadat nějak takto:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 V tomto příkladu `NewAttribute` třída může být použitý pro entitu mít pro atribut kód, ale můžete použít jen jednou u každé entity. To je zděděn z odvozené třídy při použití na základní třídu.  
  
 `AllowMultiple` a `Inherited` argumenty jsou volitelné, takže tento kód má stejný účinek:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 První `AttributeUsage` argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu. Více typů cíl může být propojený spolu s operátorem OR, následujícím způsobem:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Pokud `AllowMultiple` argument je nastaven na `true`, pak výsledný atribut lze použít více než jednou na jednu entitu, například takto:  
  
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
  
 V tomto případě `MultiUseAttr` můžete použít opakovaně, protože `AllowMultiple` je nastavena na `true`. Oba formáty pro použití více atributů jsou platné.  
  
 Pokud `Inherited` je nastavena na `false`, pak atribut není zděděn z třídy, které jsou odvozeny z třídy, která má atribut. Příklad:  
  
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
  
 V tomto případě `Attr1` neplatí pro `DClass` prostřednictvím dědičnosti.  
  
## <a name="remarks"></a>Poznámky  
 `AttributeUsage` Atribut je jedno použití atributu – jej nelze použít více než jednou pro tutéž třídu. `AttributeUsage` je alias pro <xref:System.AttributeUsageAttribute>.  
  
 Další informace najdete v tématu [přístup k atributy podle použití reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje účinek `Inherited` a `AllowMultiple` argumenty, které mají `AttributeUsage` atribut a jak mohou být uvedené vlastní atributy použité na třídu.  
  
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
  
```  
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
- [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
