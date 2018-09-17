---
title: Serializace pomocí deklarace XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 613280efc8c734c53c4af9252b4b83e2dd942f36
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45741651"
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializace pomocí deklarace XML (C#)
Toto téma popisuje, jak řídit, jestli serializace generuje deklaraci XML.  
  
## <a name="xml-declaration-generation"></a>Generování deklarace XML  
 Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklaraci XML. Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadané v poli <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda bude generovat deklarace XML, nebo ne.  
  
 Pokud serializujete na řetězec pomocí `ToString` metoda výsledného kódu XML nebude obsahovat deklaraci XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializace pomocí deklarace XML  
 Následující příklad vytvoří <xref:System.Xml.Linq.XElement>, uloží dokument k souboru a potom zobrazí soubor do konzoly:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializace bez deklarace XML  
 Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter>.  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Serializace stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
