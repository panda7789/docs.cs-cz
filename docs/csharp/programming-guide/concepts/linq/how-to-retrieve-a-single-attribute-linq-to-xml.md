---
title: "Postupy: načtení jeden atribut (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bcfdae1bd01d54baeac8946af9f2744da9a21bff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Postupy: načtení jeden atribut (technologie LINQ to XML) (C#)
Toto téma vysvětluje, jak načíst jeden atribut elementu, název atributu. To je užitečné pro zápis výrazy dotazů, ve které chcete najít element, který obsahuje konkrétní atribut.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A> Metodu <xref:System.Xml.Linq.XElement> vrací <xref:System.Xml.Linq.XAttribute> se zadaným názvem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metoda.  
  
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
  
 Tento příklad vyhledá všech potomků ve stromové struktuře s názvem `Phone`a pak najde atribut s názvem `type`.  
  
 Tento kód vytvoří následující výstup:  
  
```  
home  
work  
```  
  
## <a name="example"></a>Příklad  
 Pokud chcete k načtení hodnoty atributu, může odevzdat stejným způsobem jako s <xref:System.Xml.Linq.XElement> objekty. Následující příklad ukazuje to.  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje explicitní přetypování operátory <xref:System.Xml.Linq.XAttribute> třídy k `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, a  `GUID?`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
