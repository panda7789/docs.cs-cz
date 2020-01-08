---
title: Jak načíst jediný atribut (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 31b34bddc9e748b473641235402847991d444c39
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347495"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Jak načíst jediný atribut (LINQ to XML) (C#)
Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu. To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.  
  
 Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrací <xref:System.Xml.Linq.XAttribute> se zadaným názvem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá metodu <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
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
  
 Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone`a poté vyhledá atribut s názvem `type`.  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Pokud chcete načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u objektů <xref:System.Xml.Linq.XElement>. Následující příklad ukazuje to.  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje explicitní operátory přetypování pro třídu <xref:System.Xml.Linq.XAttribute> na `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID``GUID?`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
