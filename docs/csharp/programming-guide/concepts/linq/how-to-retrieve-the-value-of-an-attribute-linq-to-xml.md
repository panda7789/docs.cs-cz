---
title: Jak načíst hodnotu atributu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249191"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Jak načíst hodnotu atributu (LINQ do XML) (C#)
Toto téma ukazuje, jak získat hodnotu atributů. Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> Můžete přetypovat na požadovaný typ; explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ. Případně můžete využít <xref:System.Xml.Linq.XAttribute.Value%2A> ubytování. Nicméně, casting je obecně lepší přístup. Pokud přetypování atributu s hodnotou s možnou hodnotou null, kód je jednodušší psát při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky naleznete v [tématu Jak načíst hodnotu prvku (LINQ do XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu atributu, stačí přetypovat <xref:System.Xml.Linq.XAttribute> objekt na požadovaný typ.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
