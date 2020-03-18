---
title: Jak načíst jeden atribut (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168710"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Jak načíst jeden atribut (LINQ do XML) (C#)
Toto téma vysvětluje, jak načíst jeden atribut prvku, vzhledem k názvu atributu. To je užitečné pro psaní výrazů dotazu, kde chcete najít prvek, který má určitý atribut.  
  
 Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrátí <xref:System.Xml.Linq.XAttribute> se zadaným názvem.  
  
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
  
 Tento příklad vyhledá všechny potomky `Phone`ve stromu s `type`názvem a potom najde atribut s názvem .  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Pokud chcete načíst hodnotu atributu, můžete ho přetypovat, <xref:System.Xml.Linq.XElement> stejně jako u objektů. Následující příklad ukazuje to.  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje explicitní operátory <xref:System.Xml.Linq.XAttribute> přetypážení `int?` `uint`pro `uint?`třídu `ulong` `ulong?`do `float` `float?` `double` `double?` `decimal` `decimal?` `string`, `bool` `bool?`, `int`, , , , `GUID?` `long` `long?`, , , , , , , , `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, , a .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
