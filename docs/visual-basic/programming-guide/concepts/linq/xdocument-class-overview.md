---
title: Přehled třídy XDocument
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349294"
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument – Přehled třídy (Visual Basic)
Toto téma představuje třídu <xref:System.Xml.Linq.XDocument>.  
  
## <a name="overview-of-the-xdocument-class"></a>Přehled třídy XDocument  
 Třída <xref:System.Xml.Linq.XDocument> obsahuje informace potřebné pro platný dokument XML. To zahrnuje deklarace XML, instrukce pro zpracování a komentáře.  
  
 Všimněte si, že je nutné vytvořit <xref:System.Xml.Linq.XDocument> objekty pouze v případě, že požadujete konkrétní funkčnost poskytovanou <xref:System.Xml.Linq.XDocument>ou třídou. V mnoha případech můžete pracovat přímo s <xref:System.Xml.Linq.XElement>. Práce přímo s <xref:System.Xml.Linq.XElement> je jednodušší programovací model.  
  
 <xref:System.Xml.Linq.XDocument> jsou odvozeny z <xref:System.Xml.Linq.XContainer>. Proto může obsahovat podřízené uzly. <xref:System.Xml.Linq.XDocument> objektů však může mít pouze jeden podřízený <xref:System.Xml.Linq.XElement> uzel. To odráží standard XML, že v dokumentu XML může být pouze jeden kořenový element.  
  
## <a name="components-of-xdocument"></a>Komponenty XDocument  
 <xref:System.Xml.Linq.XDocument> může obsahovat následující prvky:  
  
- Jeden objekt <xref:System.Xml.Linq.XDeclaration>. <xref:System.Xml.Linq.XDeclaration> umožňuje zadat relevantní části deklarace XML: verze XML, kódování dokumentu a zda je dokument XML samostatný.  
  
- Jeden objekt <xref:System.Xml.Linq.XElement>. Toto je kořenový uzel dokumentu XML.  
  
- Libovolný počet objektů <xref:System.Xml.Linq.XProcessingInstruction>. Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.  
  
- Libovolný počet objektů <xref:System.Xml.Linq.XComment>. Komentáře budou na stejné úrovni jako kořenový element. Objekt <xref:System.Xml.Linq.XComment> nemůže být prvním argumentem v seznamu, protože není platný pro dokument XML, který by měl začít s komentářem.  
  
- Jedna <xref:System.Xml.Linq.XDocumentType> pro DTD.  
  
 Při serializaci <xref:System.Xml.Linq.XDocument>, a to i v případě, že `XDocument.Declaration` je `null`, výstup bude obsahovat deklarace XML, pokud má zapisovač `Writer.Settings.OmitXmlDeclaration` nastaven na `false` (výchozí).  
  
 Ve výchozím nastavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nastaví verzi na "1,0" a nastaví kódování na UTF-8.  
  
## <a name="using-xelement-without-xdocument"></a>Použití XElement bez XDocument  
 Jak už jsme uvedli, třída <xref:System.Xml.Linq.XElement> je hlavní třídou v programovacím rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. V mnoha případech aplikace nebude vyžadovat vytvoření dokumentu. Pomocí třídy <xref:System.Xml.Linq.XElement> lze vytvořit strom XML, přidat do něj další stromy XML, upravit strom XML a uložit jej.  
  
## <a name="using-xdocument"></a>Použití XDocument  
 Chcete-li vytvořit <xref:System.Xml.Linq.XDocument>, použijte funkční konstrukci stejným způsobem jako při vytváření objektů <xref:System.Xml.Linq.XElement>.  
  
 Následující kód vytvoří objekt <xref:System.Xml.Linq.XDocument> a jeho přidružené objekty v kontejneru.  
  
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
  
 Při kontrole souboru Test. XML získáte následující výstup:  
  
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

- [Přehled programování LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
