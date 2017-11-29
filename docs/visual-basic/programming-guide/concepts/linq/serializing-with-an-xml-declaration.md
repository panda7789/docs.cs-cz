---
title: Serializace s deklarace XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8544157104b202a36f2ef75b069bcdd297b9158
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serializace s deklarace XML (Visual Basic)
Toto téma popisuje, jak řídit, jestli serializace generuje deklarace XML.  
  
## <a name="xml-declaration-generation"></a>Generování deklarace XML  
 K serializaci <xref:System.IO.File> nebo <xref:System.IO.TextWriter> pomocí <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> metoda nebo <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> metoda generuje deklarace XML. Při serializaci do <xref:System.Xml.XmlWriter>, nastavení zapisovače (zadaný v <xref:System.Xml.XmlWriterSettings> objektu) určete, zda se vygeneruje deklarace XML, nebo ne.  
  
 Pokud je serializována na řetězec pomocí `ToString` metoda, výsledná XML nebude obsahovat deklarace XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializace s deklarace XML  
 Následující příklad vytvoří <xref:System.Xml.Linq.XElement>dokument uloží do souboru a potom zobrazí soubor do konzoly:  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializace bez deklarace XML  
 Následující příklad ukazuje, jak uložit <xref:System.Xml.Linq.XElement> k <xref:System.Xml.XmlWriter>.  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Serializace XML stromů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
