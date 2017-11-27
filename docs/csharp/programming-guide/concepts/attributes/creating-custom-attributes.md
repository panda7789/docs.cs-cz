---
title: "Vytváření vlastních atributů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 `AttributeUsage`má parametr s názvem `AllowMultiple`, pomocí kterého můžete nastavit vlastní atribut jedno použití nebo multiuse. V následujícím příkladu kódu je vytvořen multiuse atribut.  
  
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
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)  
 [Zápis vlastních atributů](../../../../standard/attributes/writing-custom-attributes.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
