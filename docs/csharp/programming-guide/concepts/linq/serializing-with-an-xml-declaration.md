---
title: Serializace s deklarací XML (C#)
description: Přečtěte si o konfiguracích, ve kterých serializace v jazyce C# generuje deklaraci XML, včetně serializace do souboru, TextWriter a XmlWriter.
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 7e91b61f037d28149f7c2355f4233dc319b54627
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302357"
---
# <a name="serializing-with-an-xml-declaration-c"></a>Serializace s deklarací XML (C#)
Toto téma popisuje, jak určit, zda serializace generuje deklaraci XML.  
  
## <a name="xml-declaration-generation"></a>Generování deklarace XML  
 Serializace do <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metody nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metody generuje deklaraci XML. Při serializaci do <xref:System.Xml.XmlWriter> , nastavení zapisovače (určené v <xref:System.Xml.XmlWriterSettings> objektu) určuje, zda je generována deklarace XML.  
  
 Pokud provádíte serializaci do řetězce pomocí `ToString` metody, výsledný kód XML nebude obsahovat deklaraci XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializace pomocí deklarace XML  
 Následující příklad vytvoří <xref:System.Xml.Linq.XElement> , uloží dokument do souboru a pak vytiskne soubor do konzoly:  
  
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
 Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> do <xref:System.Xml.XmlWriter> .  
  
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
  
## <a name="see-also"></a>Viz také:

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
