---
title: 'Postupy: načtení hodnoty atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: a78cda390cc7b3d489cfda212cf8fb8111e4dde2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501501"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Postupy: načtení hodnoty atributu (LINQ to XML) (C#)
Toto téma ukazuje, jak získat hodnoty atributů. Existují dva hlavní způsoby: můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu převede obsah elementu nebo atributu do zadaného typu. Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost. Přetypování je však obvykle bude vhodnější. Pokud vložíte atribut na typ připouštějící hodnotu Null, kód je jednodušší zápis při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky najdete v tématu [postupy: načtení hodnoty elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 K načtení hodnoty atributu, jenom udělíte <xref:System.Xml.Linq.XAttribute> objekt požadovaného typu.  
  
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
 Následující příklad ukazuje způsob k načtení hodnoty atributu, kde se příslušný atribut nachází v oboru názvů. Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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

- [Osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
