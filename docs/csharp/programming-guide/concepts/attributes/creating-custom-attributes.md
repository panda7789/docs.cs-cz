---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 5a846771eb26e3760e3f47458b862356f4da1ae6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503703"
---
# <a name="creating-custom-attributes-c"></a>Vytváření vlastních atributů (C#)
Můžete vytvořit vlastní atributy definováním třídy atributu, třídu, která je odvozena přímo nebo nepřímo z <xref:System.Attribute>, díky kterému budou Identifikace definice atributu v metadatech rychlé a snadné. Předpokládejme, že chcete typy značek s názvem programátora, který napsal typu. Můžete třeba definovat vlastní `Author` třídy atributů:  
  
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
  
 Název třídy je název atributu, `Author`. Je odvozen z `System.Attribute`, tak, aby byl třídu vlastního atributu. Vlastní atribut poziční parametry jsou parametry konstruktoru. V tomto příkladu `name` je poziční parametr. Žádné vlastnosti nebo pole veřejné čtení a zápis jsou pojmenované parametry. V takovém případě `version` je pouze s názvem parametru. Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut je platný pouze pro třídy a `struct` deklarace.  
  
 Tento nový atribut můžete použít takto:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` nemá parametr pojmenovaný `AllowMultiple`, pomocí které můžete vytvořit vlastní atribut jedno použití nebo multiuse. V následujícím příkladu kódu je vytvořen multiuse atribut.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 V následujícím příkladu kódu se více atributů stejného typu aplikován na třídu.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  Pokud vaše třída atributů obsahuje vlastnost, musí být tuto vlastnost pro čtení i zápis.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection>  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
- [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)  
- [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
