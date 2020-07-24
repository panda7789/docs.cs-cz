---
title: Jak načíst jediný atribut (LINQ to XML) (C#)
description: Naučte se, jak použít LINQ to XML načíst jeden atribut prvku v jazyce C# s ohledem na název atributu.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103428"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Jak načíst jediný atribut (LINQ to XML) (C#)
Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu. To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A>Metoda <xref:System.Xml.Linq.XElement> třídy vrací se <xref:System.Xml.Linq.XAttribute> zadaným názvem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metodu.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone` a pak vyhledá atribut s názvem `type` .  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u s <xref:System.Xml.Linq.XElement> objekty. Následující příklad ukazuje to.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje explicitní operátory přetypování pro <xref:System.Xml.Linq.XAttribute> třídu na `string` , `bool` ,,, `bool?` `int` `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,, a.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
