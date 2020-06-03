---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389562"
---
# <a name="creating-custom-attributes-c"></a>Vytváření vlastních atributů (C#)
Můžete vytvořit vlastní atributy definováním třídy atributů, třídy, která je odvozena přímo nebo nepřímo z <xref:System.Attribute> , což umožňuje rychlou a jednoduchou identifikaci definic atributů v metadatech. Předpokládejme, že chcete označit typy s názvem programátora, který typ napsal. Je možné definovat vlastní `Author` třídu atributu:  
  
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
  
 Název třídy je název atributu, `Author` . Je odvozen z `System.Attribute` , takže se jedná o vlastní třídu atributu. Parametry konstruktoru jsou poziční parametry vlastního atributu. V tomto příkladu `name` je poziční parametr. Všechna veřejná pole nebo vlastnosti pro čtení i zápis se nazývají parametry. V tomto případě `version` je jediným pojmenovaným parametrem. Všimněte si, že použití `AttributeUsage` atributu pro nastavení `Author` atributu je platné pouze pro třídu a `struct` deklarace.  
  
 Tento nový atribut můžete použít následujícím způsobem:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`má pojmenovaný parametr, `AllowMultiple` pomocí kterého můžete vytvořit vlastní atribut s jedním použitím nebo Multiuse. V následujícím příkladu kódu je vytvořen atribut Multiuse.  
  
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
- [Průvodce programováním v C#](../../index.md)
- [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy (C#)](./index.md)
- [Přístup k atributům pomocí reflexe (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
