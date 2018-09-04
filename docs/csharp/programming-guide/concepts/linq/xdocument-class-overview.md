---
title: Přehled třídy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 0d182593cfedd30042c4e3a5d776bb00ce267ff7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504855"
---
# <a name="xdocument-class-overview-c"></a>Přehled třídy XDocument (C#)
Toto téma představuje <xref:System.Xml.Linq.XDocument> třídy.  
  
## <a name="overview-of-the-xdocument-class"></a>Přehled třídy XDocument  
 <xref:System.Xml.Linq.XDocument> Třída obsahuje informace potřebné pro platný dokument XML. To zahrnuje deklarace XML, zpracování pokyny a komentáře.  
  
 Všimněte si, že budete muset vytvořit <xref:System.Xml.Linq.XDocument> objektů, pokud potřebujete konkrétní funkce poskytované službou <xref:System.Xml.Linq.XDocument> třídy. V mnoha případech platí, může spolupracovat přímo s <xref:System.Xml.Linq.XElement>. Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.  
  
 <xref:System.Xml.Linq.XDocument> je odvozen od <xref:System.Xml.Linq.XContainer>. Proto může obsahovat podřízené uzly. Ale <xref:System.Xml.Linq.XDocument> objekty mohou mít pouze jeden podřízený prvek <xref:System.Xml.Linq.XElement> uzlu. To odpovídá standardu XML mohou být pouze jeden kořenový element v dokumentu XML.  
  
## <a name="components-of-xdocument"></a>Součástí XDocument  
 <xref:System.Xml.Linq.XDocument> Může obsahovat následující prvky:  
  
-   Jeden <xref:System.Xml.Linq.XDeclaration> objektu. <xref:System.Xml.Linq.XDeclaration> Umožňuje určit, které jsou relevantní části deklarace XML: XML version, kódování dokumentu, a zda je samostatný dokumentu XML.  
  
-   Jeden <xref:System.Xml.Linq.XElement> objektu. Toto je kořenový uzel dokumentu XML.  
  
-   Libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objekty. Instrukce pro zpracování komunikuje informace k aplikaci, která zpracovává XML.  
  
-   Libovolný počet <xref:System.Xml.Linq.XComment> objekty. Komentáře se na stejné úrovni jako kořenový element. <xref:System.Xml.Linq.XComment> Objektu nemůže být prvním argumentem v seznamu, protože není platný pro začínat komentář dokumentu XML.  
  
-   Jeden <xref:System.Xml.Linq.XDocumentType> pro DTD.  
  
 Při serializaci <xref:System.Xml.Linq.XDocument>i v případě `XDocument.Declaration` je `null`, výstup bude mít deklarace XML, pokud má modul pro zápis `Writer.Settings.OmitXmlDeclaration` nastavena na `false` (výchozí).  
  
 Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi "1.0" a nastaví kódování na "utf-8".  
  
## <a name="using-xelement-without-xdocument"></a>Pomocí XElement bez XDocument  
 Jak už jsme zmínili, <xref:System.Xml.Linq.XElement> třída je hlavní třída v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní. V mnoha případech se vaše aplikace nebude vyžadovat vytvoření dokumentu. S použitím <xref:System.Xml.Linq.XElement> třídy, můžete vytvořit stromu XML, k němu přidat další stromů XML, upravte stromu XML a uložit jej.  
  
## <a name="using-xdocument"></a>Pomocí XDocument  
 K vytvoření <xref:System.Xml.Linq.XDocument>, použijte funkční konstrukce, stejně jako máte k sestavení kompletních <xref:System.Xml.Linq.XElement> objekty.  
  
 Následující kód vytvoří <xref:System.Xml.Linq.XDocument> objektu a jeho přidruženého obsažené objekty.  
  
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
  
 Při zkoumání souboru test.xml, získáte následující výstup:  
  
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

- [Přehled LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
