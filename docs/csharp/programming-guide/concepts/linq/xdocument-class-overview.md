---
title: Přehled třídy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590840"
---
# <a name="xdocument-class-overview-c"></a>Přehled třídy XDocument (C#)
Toto téma <xref:System.Xml.Linq.XDocument> představuje třídu.  
  
## <a name="overview-of-the-xdocument-class"></a>Přehled třídy XDocument  
 Třída <xref:System.Xml.Linq.XDocument> obsahuje informace potřebné pro platný dokument XML. To zahrnuje deklaraci XML, pokyny pro zpracování a komentáře.  
  
 Všimněte si, že <xref:System.Xml.Linq.XDocument> stačí vytvořit objekty, pokud požadujete konkrétní funkce poskytované třídy. <xref:System.Xml.Linq.XDocument> V mnoha případech můžete pracovat <xref:System.Xml.Linq.XElement>přímo s . Práce přímo <xref:System.Xml.Linq.XElement> s je jednodušší programovací model.  
  
 <xref:System.Xml.Linq.XDocument>pochází z <xref:System.Xml.Linq.XContainer>. Proto může obsahovat podřízené uzly. Objekty <xref:System.Xml.Linq.XDocument> však mohou <xref:System.Xml.Linq.XElement> mít pouze jeden podřízený uzel. To odráží standard XML, že v dokumentu XML může být pouze jeden kořenový prvek.  
  
## <a name="components-of-xdocument"></a>Součásti XDocument  
 A <xref:System.Xml.Linq.XDocument> může obsahovat následující prvky:  
  
- Jeden <xref:System.Xml.Linq.XDeclaration> objekt. <xref:System.Xml.Linq.XDeclaration>umožňuje zadat příslušné části deklarace XML: verzi XML, kódování dokumentu a to, zda je dokument XML samostatný.  
  
- Jeden <xref:System.Xml.Linq.XElement> objekt. Toto je kořenový uzel dokumentu XML.  
  
- Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objektů. Instrukce zpracování sděluje informace aplikaci, která zpracovává XML.  
  
- Libovolný počet <xref:System.Xml.Linq.XComment> objektů. Komentáře budou na stejné úrovni kořenový prvek. Objekt <xref:System.Xml.Linq.XComment> nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML, který má začínat komentářem.  
  
- Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.  
  
 Pokud serializujete <xref:System.Xml.Linq.XDocument>, i `XDocument.Declaration` `null`když je , výstup bude mít `Writer.Settings.OmitXmlDeclaration` deklaraci `false` XML, pokud je zapisovatel nastaven na (výchozí).  
  
 Ve výchozím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastavení nastaví verzi na "1.0" a nastaví kódování na "utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Použití prvku XElement bez prvku XDocument  
 Jak již bylo <xref:System.Xml.Linq.XElement> zmíněno, třída je [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] hlavní třídou v programovacím rozhraní. V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu. Pomocí <xref:System.Xml.Linq.XElement> třídy můžete vytvořit strom XML, přidat do něj další stromy XML, upravit strom XML a uložit.  
  
## <a name="using-xdocument"></a>Použití XDocument  
 Chcete-li <xref:System.Xml.Linq.XDocument>vytvořit , použijte funkční konstrukce, <xref:System.Xml.Linq.XElement> stejně jako to děláte k vytvoření objektů.  
  
 Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objekt a jeho přidružené obsažené objekty.  
  
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
  
 Při kontrole souboru test.xml získáte následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
