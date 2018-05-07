---
title: 'Postupy: načtení hodnoty atributu (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 224ba9ba47d68afd7c29d0f33fe20d290d0b5ef5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Postupy: načtení hodnoty atributu (technologie LINQ to XML) (C#)
Toto téma ukazuje, jak získat hodnotu atributů. Existují dva hlavní způsoby: může odevzdat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitní převod potom převede obsah elementu nebo atributu zadaného typu. Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost. Přetypování je ale obecně lepší přístup. Pokud jste přetypovat atribut typu s povolenou hodnotou Null, kód je jednodušší při načítání hodnoty atributu, který může nebo nemusí existovat zápis. Příklady tento postup najdete v tématu [postupy: načtení hodnoty elementu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 K načtení hodnoty atributu, je právě přetypovat <xref:System.Xml.Linq.XAttribute> objekt, který má požadovaný typ.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst hodnotu atributu kde atributu je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
abcde  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
