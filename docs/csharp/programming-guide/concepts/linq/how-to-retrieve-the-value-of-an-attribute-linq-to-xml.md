---
title: 'Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 635aee3bd08618b94fb5c091f8eef212c067acef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253385"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)
V tomto tématu se dozvíte, jak získat hodnotu atributů. Existují dva hlavní způsoby: Můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ. Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost. Přetypování je však všeobecně lepším přístupem. Pokud přetypování atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky naleznete v tématu [How to: Načtení hodnoty elementu (LINQ to XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu atributu, stačí přetypování <xref:System.Xml.Linq.XAttribute> objektu na požadovaný typ.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
