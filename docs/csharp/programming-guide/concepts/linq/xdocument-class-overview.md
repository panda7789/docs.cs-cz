---
title: XDocument – Přehled třídy (C#)
description: Třída XDocument v jazyce C# obsahuje informace potřebné pro platný dokument XML, včetně deklarace XML, instrukcí pro zpracování a komentářů.
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 6d522cef25e99e4a5ea54e644855c8dfa7a05f4a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302188"
---
# <a name="xdocument-class-overview-c"></a>XDocument – Přehled třídy (C#)
Toto téma představuje <xref:System.Xml.Linq.XDocument> třídu.  
  
## <a name="overview-of-the-xdocument-class"></a>Přehled třídy XDocument  
 <xref:System.Xml.Linq.XDocument>Třída obsahuje informace potřebné pro platný dokument XML. To zahrnuje deklarace XML, instrukce pro zpracování a komentáře.  
  
 Všimněte si, že je třeba vytvořit <xref:System.Xml.Linq.XDocument> objekty pouze v případě, že požadujete konkrétní funkce poskytované <xref:System.Xml.Linq.XDocument> třídou. V mnoha případech můžete pracovat přímo s <xref:System.Xml.Linq.XElement> . Práce přímo s nástrojem <xref:System.Xml.Linq.XElement> je jednodušší programovací model.  
  
 <xref:System.Xml.Linq.XDocument>je odvozen z <xref:System.Xml.Linq.XContainer> . Proto může obsahovat podřízené uzly. Nicméně <xref:System.Xml.Linq.XDocument> objekty mohou mít pouze jeden podřízený <xref:System.Xml.Linq.XElement> uzel. To odráží standard XML, že v dokumentu XML může být pouze jeden kořenový element.  
  
## <a name="components-of-xdocument"></a>Komponenty XDocument  
 <xref:System.Xml.Linq.XDocument>Může obsahovat následující prvky:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> objekt. <xref:System.Xml.Linq.XDeclaration>umožňuje zadat relevantní části deklarace XML: verze XML, kódování dokumentu a zda je dokument XML samostatný.  
  
- Jeden <xref:System.Xml.Linq.XElement> objekt. Toto je kořenový uzel dokumentu XML.  
  
- Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objektů. Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.  
  
- Libovolný počet <xref:System.Xml.Linq.XComment> objektů. Komentáře budou na stejné úrovni jako kořenový element. <xref:System.Xml.Linq.XComment>Objekt nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML, aby začínat komentářem.  
  
- Jednu <xref:System.Xml.Linq.XDocumentType> pro DTD.  
  
 Při serializaci <xref:System.Xml.Linq.XDocument> , i když `XDocument.Declaration` je `null` , výstup bude obsahovat deklaraci XML, pokud zapisovač je `Writer.Settings.OmitXmlDeclaration` nastaven na `false` (výchozí).  
  
 Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi na "1,0" a nastaví kódování na UTF-8.  
  
## <a name="using-xelement-without-xdocument"></a>Použití XElement bez XDocument  
 Jak už jsme uvedli, <xref:System.Xml.Linq.XElement> Třída je hlavní třídou v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovacím rozhraní. V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu. Pomocí <xref:System.Xml.Linq.XElement> třídy můžete vytvořit strom XML, přidat do něj další stromy XML, upravit strom XML a uložit jej.  
  
## <a name="using-xdocument"></a>Použití XDocument  
 Chcete-li vytvořit <xref:System.Xml.Linq.XDocument> , použijte funkční konstrukci stejným způsobem jako při vytváření <xref:System.Xml.Linq.XElement> objektů.  
  
 Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objekt a jeho přidružené objekty v kontejneru.  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 Po prohlédnutí test.xml souboru se zobrazí následující výstup:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
