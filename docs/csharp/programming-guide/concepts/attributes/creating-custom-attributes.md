---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595415"
---
# <a name="creating-custom-attributes-c"></a>Vytváření vlastních atributů (C#)
Vlastní atributy můžete vytvořit definováním třídy atributů, třídy, která <xref:System.Attribute>je přímo nebo nepřímo odvozena z , což umožňuje rychlou a snadnou identifikaci definic atributů v metadatech. Předpokládejme, že chcete označit typy s názvem programátora, který napsal typ. Můžete definovat vlastní `Author` třídu atributů:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Název třídy je název atributu . `Author` Je odvozen od `System.Attribute`, takže se jedná o vlastní třídu atributů. Parametry konstruktoru jsou poziční parametry vlastního atributu. V tomto `name` příkladu je poziční parametr. Všechna veřejná pole pro čtení a zápis nebo vlastnosti jsou pojmenovány parametry. V tomto `version` případě je pouze pojmenovaný parametr. Všimněte si `AttributeUsage` použití atributu, aby byl `Author` `struct` atribut platný pouze pro třídu a deklarace.  
  
 Tento nový atribut můžete použít následujícím způsobem:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`má pojmenovaný parametr `AllowMultiple`, pomocí kterého můžete vytvořit vlastní atribut na jedno použití nebo vícepoužití. V následujícím příkladu kódu je vytvořen víceúčelový atribut.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 V následujícím příkladu kódu je pro třídu použito více atributů stejného typu.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- [Programovací příručka jazyka C#](../../index.md)
- [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](./index.md)
- [Přístup k atributům pomocí reflexe (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](./attributeusage.md)
