---
title: Typy uzlů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
ms.openlocfilehash: 5e11d61e16659ac1a8ca1b0b2c0d493ffdad5621
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282061"
---
# <a name="types-of-xml-nodes"></a>Typy uzlů XML
Když je dokument XML čten do paměti jako strom uzlů, typy uzlů pro uzly jsou určeny při vytváření uzlů. XML model DOM (Document Object Model) (DOM) má několik druhů typů uzlů určených konsorcium World Wide Web (W3C) a uvedené v části 1.1.1 model struktury DOM. V následující tabulce jsou uvedeny typy uzlů, objekt přiřazený k tomuto typu uzlu a stručný popis každého z nich.  
  
|Typ uzlu DOM|Objekt|Popis|  
|-------------------|------------|-----------------|  
|Dokument|<xref:System.Xml.XmlDocument>|Kontejner všech uzlů ve stromu Je také označován jako kořenový adresář dokumentu, který není vždy stejný jako kořenový element.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Dočasný vaku obsahující jeden nebo více uzlů bez stromové struktury.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Představuje `<!DOCTYPE…>` uzel.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Představuje nerozbalený textový odkaz na entitu.|  
|Prvek|<xref:System.Xml.XmlElement>|Představuje uzel elementu.|  
|ATTR|<xref:System.Xml.XmlAttribute>|Je atributem elementu.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Je uzel instrukcí pro zpracování.|  
|Komentář|<xref:System.Xml.XmlComment>|Uzel komentáře|  
|Text|<xref:System.Xml.XmlText>|Text patřící k elementu nebo atributu|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Reprezentuje CDATA.|  
|Entita|<xref:System.Xml.XmlEntity>|Představuje `<!ENTITY…>` deklarace v dokumentu XML, buď z vnitřní podmnožiny definice typu dokumentu (DTD), nebo z externích definicí a entit parametrů.|  
|Notace|<xref:System.Xml.XmlNotation>|Představuje notaci deklarovaný v DTD.|  
  
 I když je atribut (*ATTR*) uveden v části 1,2 konsorcia W3C úrovně 1 v části základní rozhraní jako uzel, není považován za podřízený uzel žádného elementu.  
  
 Následující tabulka uvádí další typy uzlů, které nejsou definovány konsorciem W3C, ale jsou k dispozici pro použití v modelu Microsoft .NET Framework Object Model jako výčty **XmlNodeType** . Proto pro tyto typy uzlů neexistuje žádný shodný sloupec typu uzlu modelu DOM.  
  
|Typ uzlu|Popis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Představuje uzel deklarace `<?xml version="1.0"…>` .|  
|<xref:System.Xml.XmlSignificantWhitespace>|Představuje významné prázdné znaky, což je prázdné místo ve smíšeném obsahu.|  
|<xref:System.Xml.XmlWhitespace>|Představuje prázdné místo v obsahu elementu.|  
|EndElement|Vrátí se, když se **XmlReader** dostane na konec elementu.<br /><br /> Příklad XML:**\</item>**<br /><br /> Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Vrátí se, když se **XmlReader** vrátí na konec náhrady entity v důsledku volání metody <xref:System.Xml.XmlReader.ResolveEntity%2A> . Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
  
 Chcete-li zobrazit příklad kódu, který čte v jazyce XML a používá v typech uzlů konstrukci Case pro tisk informací o uzlu a jeho obsahu, přečtěte si téma <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A> .  
  
 Další informace o hierarchii objektů typů uzlů a jejich ekvivalentních názvů objektů naleznete v tématu [XML model DOM (Document Object Model) (DOM) hierarchii](xml-document-object-model-dom-hierarchy.md). Další informace o objektech vytvořených ve stromové struktuře uzlu najdete v tématu [mapování hierarchie objektů na data XML](mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
