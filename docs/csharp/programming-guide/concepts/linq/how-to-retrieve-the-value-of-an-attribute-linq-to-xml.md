---
title: 'Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 94cab43571f7ade55155e7925975f253e452ceb7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485003"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)
Toto téma ukazuje, jak získat hodnoty atributů. Existují dva hlavní způsoby: Můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu převede obsah elementu nebo atributu do zadaného typu. Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost. Přetypování je však obvykle bude vhodnější. Pokud vložíte atribut na typ připouštějící hodnotu Null, kód je jednodušší zápis při načítání hodnoty atributu, který může nebo nemusí existovat. Příklady této techniky najdete v tématu [jak: Načtení hodnoty elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
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
 Následující příklad ukazuje způsob k načtení hodnoty atributu, kde se příslušný atribut nachází v oboru názvů. Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- [Osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
