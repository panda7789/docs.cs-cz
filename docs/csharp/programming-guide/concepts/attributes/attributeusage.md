---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9351ee10b523145ace1249bf17388da0cdba277
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)
Určuje, jak lze použít třídu vlastního atributu. `AttributeUsage`je atribut, který můžete použít pro vlastní atribut definice řídit, jak můžete použít nový atribut. Výchozí nastavení se při použití explicitně vypadat například takto:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 V tomto příkladu `NewAttribute` třídy lze použít na všechny možné atribut kód entity, ale lze použít pouze jednou pro každé entity. Zdědí odvozené třídy při použití základní třídy.  
  
 `AllowMultiple` a `Inherited` jsou argumenty nepovinné, takže tento kód má stejný účinek:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 První `AttributeUsage` argument musí být jeden či více elementů <xref:System.AttributeTargets> výčtu. Více typy cíle může být propojený společně s operátoru OR takto:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 Pokud `AllowMultiple` argument je nastaven na hodnotu `true`, pak výsledné atribut lze použít více než jednou k jedné entity, jako je tento:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 V takovém případě `MultiUseAttr` můžete použít opakovaně, protože `AllowMultiple` je nastaven na `true`. Platné jsou oba formáty pro použití více atributů.  
  
 Pokud `Inherited` je nastaven na `false`, pak atribut není zdědí třídy, které jsou odvozeny od třídy, který je nastavený atribut. Příklad:  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 V takovém případě `Attr1` neplatí pro `DClass` prostřednictvím dědičnosti.  
  
## <a name="remarks"></a>Poznámky  
 `AttributeUsage` Se o jedno použití atribut – jej nelze použít více než jednou pro stejnou třídu. `AttributeUsage`je alias <xref:System.AttributeUsageAttribute>.  
  
 Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje účinek `Inherited` a `AllowMultiple` argumenty, které mají `AttributeUsage` atribut a jak mohou být uvedené vlastních atributů použitých na třídu.  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
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
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)  
 [Atributy](../../../../../docs/standard/attributes/index.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Vytváření vlastních atributů (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
