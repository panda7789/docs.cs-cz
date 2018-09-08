---
title: Typy uzlů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623583f16c23b55c16f648fedcd039ca36f73b1f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129310"
---
# <a name="types-of-xml-nodes"></a>Typy uzlů XML
Při čtení dokumentu XML do paměti jako strom uzly jsou typy uzlů pro uzly rozhodla vytvořené uzly. Má několik druhů typy uzlů, určené World Wide Web Consortium (W3C) XML Document Object Model (DOM) a uvedené v části 1.1.1 strukturu modelu DOM. Následující tabulka uvádí typy uzlů, přiřazené k typu uzlu a krátký popis každého objektu.  
  
|Typ uzlu modelu DOM|Objekt|Popis|  
|-------------------|------------|-----------------|  
|Dokument|<xref:System.Xml.XmlDocument>|Kontejner všech uzlů ve stromu. To se také nazývá kořen dokumentu, který není vždy stejný jako kořenový element.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Dočasné kontejner obsahující jeden nebo více uzlů bez žádné stromová struktura.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Představuje `<!DOCTYPE…>` uzlu.|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Představuje odkaz na text bez rozšířit entity.|  
|Prvek|<xref:System.Xml.XmlElement>|Představuje uzel elementu.|  
|attr|<xref:System.Xml.XmlAttribute>|Představuje atribut prvku.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Je uzel zpracování instrukcí.|  
|Komentář|<xref:System.Xml.XmlComment>|Uzel komentáře.|  
|Text|<xref:System.Xml.XmlText>|Text, který patří k elementu nebo atributu.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Představuje CDATA.|  
|Entity|<xref:System.Xml.XmlEntity>|Představuje `<!ENTITY…>` deklarace ve formátu XML dokumentu, buď z podsadě interní dokumentu typ definice (DTD), nebo externí specifikace DTD a parametr entity.|  
|Zápis|<xref:System.Xml.XmlNotation>|Představuje notace deklarované v DTD.|  
  
 I když atribut (*attr*) je uveden v 1. úrovně modelu DOM W3C části 1.2 základní rozhraní jako uzel, není to považováno za podřízené libovolného uzlu elementu.  
  
 Následující tabulka uvádí typy dalšího uzlu nejsou definovány parametrem W3C, ale jsou k dispozici pro použití v objektovém modelu rozhraní Microsoft .NET Framework jako **XmlNodeType** výčty. Proto neexistuje žádný odpovídající modelu DOM uzel typu sloupec pro tyto typy uzlů.  
  
|Typ uzlu|Popis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Představuje uzel deklarace `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Představuje významnou mezeru, což je prázdné místo v smíšený obsah.|  
|<xref:System.Xml.XmlWhitespace>|Představuje mezer v obsahu elementu.|  
|Vlastnost EndElement|Vrátí, když **XmlReader** získá koncový prvek.<br /><br /> Ukázkový soubor XML:  **\< /položka >**<br /><br /> Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Vrátí, když **XmlReader** získá za účelem nahrazení entity jako výsledek volání <xref:System.Xml.XmlReader.ResolveEntity%2A>. Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
  
 Chcete-li zobrazit příklad kódu, který čte ve formátu XML a používá případu konstrukce u typů uzlů na tiskové informace o uzlu a její obsah, najdete v článku <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Další informace o hierarchii objektů typy uzlů a jejich název ekvivalentních objektů naleznete v tématu [hierarchii XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Další informace o objekty vytvořené v uzlu stromu, naleznete v tématu [mapování hierarchie objektů na XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
