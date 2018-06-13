---
title: Vytváření vlastních atributů (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c1532d52e1e69c83a04ead7b771cd460f43d56b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315877"
---
# <a name="creating-custom-attributes-c"></a>Vytváření vlastních atributů (C#)
Můžete vytvořit vlastní atributy definováním třídy atributu, třídu odvozenou z přímo nebo nepřímo <xref:System.Attribute>, které díky Identifikace definice atributu v metadatech rychlé a snadné. Předpokládejme, že chcete typy značky s názvem programátory, kteří napsali typu. Můžete třeba definovat vlastní `Author` třídy atributů:  
  
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
  
 Název třídy je název atributu, `Author`. Je odvozený od `System.Attribute`, takže je třídu vlastního atributu. V konstruktoru parametry jsou vlastní atribut poziční parametry. V tomto příkladu `name` je parametr poziční. Všechny vlastnosti nebo veřejná pole pro čtení a zápis jsou pojmenované parametry. V takovém případě `version` je jediným s názvem parametru. Všimněte si použití `AttributeUsage` atribut, aby `Author` atribut platná pouze pro třídy a `struct` deklarace.  
  
 Tento nový atribut můžete použít takto:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` má parametr s názvem `AllowMultiple`, pomocí kterého můžete nastavit vlastní atribut jedno použití nebo multiuse. V následujícím příkladu kódu je vytvořen multiuse atribut.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 V následujícím příkladu kódu je na třídu použít víc atributů stejného typu.  
  
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
>  Pokud vaše třídy atributů obsahuje vlastnost, vlastnosti musí být pro čtení a zápis.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
