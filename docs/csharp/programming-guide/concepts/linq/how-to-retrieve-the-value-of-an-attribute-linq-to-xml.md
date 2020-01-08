---
title: Jak načíst hodnotu atributu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347437"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Jak načíst hodnotu atributu (LINQ to XML) (C#)
V tomto tématu se dozvíte, jak získat hodnotu atributů. Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> můžete přetypovat na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ. Alternativně můžete použít vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>. Přetypování je však všeobecně lepším přístupem. Pokud přetypování atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky naleznete v tématu [jak načíst hodnotu prvku (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Chcete-li načíst hodnotu atributu, stačí přetypování objektu <xref:System.Xml.Linq.XAttribute> na požadovaný typ.  
  
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
