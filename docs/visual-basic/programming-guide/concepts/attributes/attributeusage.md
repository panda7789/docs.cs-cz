---
title: AttributeUsage (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aef00d201c3dea82f67395bee0d85f8989afa01e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Určuje, jak lze použít třídu vlastního atributu. `AttributeUsage`je atribut, který můžete použít pro vlastní atribut definice řídit, jak můžete použít nový atribut. Výchozí nastavení se při použití explicitně vypadat například takto:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 V tomto příkladu `NewAttribute` třídy lze použít na všechny možné atribut kód entity, ale lze použít pouze jednou pro každé entity. Zdědí odvozené třídy při použití základní třídy.  
  
 `AllowMultiple` a `Inherited` jsou argumenty nepovinné, takže tento kód má stejný účinek:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 První `AttributeUsage` argument musí být jeden či více elementů <xref:System.AttributeTargets> výčtu. Více typy cíle může být propojený společně s operátoru OR takto:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Pokud `AllowMultiple` argument je nastaven na hodnotu `true`, pak výsledné atribut lze použít více než jednou k jedné entity, jako je tento:  
  
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
  
 V takovém případě `MultiUseAttr` můžete použít opakovaně, protože `AllowMultiple` je nastaven na `true`. Platné jsou oba formáty pro použití více atributů.  
  
 Pokud `Inherited` je nastaven na `false`, pak atribut není zdědí třídy, které jsou odvozeny od třídy, který je nastavený atribut. Příklad:  
  
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
  
 V takovém případě `Attr1` neplatí pro `DClass` prostřednictvím dědičnosti.  
  
## <a name="remarks"></a>Poznámky  
 `AttributeUsage` Se o jedno použití atribut – jej nelze použít více než jednou pro stejnou třídu. `AttributeUsage`je alias <xref:System.AttributeUsageAttribute>.  
  
 Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje účinek `Inherited` a `AllowMultiple` argumenty, které mají `AttributeUsage` atribut a jak mohou být uvedené vlastních atributů použitých na třídu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atributy](https://msdn.microsoft.com/library/5x6cd29c)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
