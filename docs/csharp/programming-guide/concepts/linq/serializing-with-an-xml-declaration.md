---
title: Serializace s deklarací XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483480"
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializace s deklarací XML (C#)
Toto téma popisuje, jak řídit, zda serializace generuje deklaraci XML.  
  
## <a name="xml-declaration-generation"></a>Generování deklarace XML  
 Serializace na <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> nebo metody generuje deklaraci XML. Při serializaci do <xref:System.Xml.XmlWriter>aplikace určují nastavení pro <xref:System.Xml.XmlWriterSettings> zápis (zadané v objektu), zda je deklarace XML generována či nikoli.  
  
 Pokud serializujete řetězec pomocí `ToString` metody, výsledný kód XML nebude obsahovat deklaraci XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializace pomocí deklarace XML  
 Následující příklad vytvoří <xref:System.Xml.Linq.XElement>soubor , uloží dokument do souboru a pak jej vytiskne do konzoly:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializace bez deklarace XML  
 Následující příklad ukazuje, jak <xref:System.Xml.Linq.XElement> uložit <xref:System.Xml.XmlWriter>do .  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
