---
title: Přehled třídy XDocument (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: f9a531b9e90a8d6511dd0a2c6fc3131c9bfe1e89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834280"
---
# <a name="xdocument-class-overview-visual-basic"></a>Přehled třídy XDocument (Visual Basic)
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
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
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
doc.Save("test.xml")  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
