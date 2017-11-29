---
title: "Typy uzlů XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a>Typy uzlů XML
Pokud dokument XML je pro čtení do paměti jako strom uzlů, typy uzlů pro uzly se rozhodla při vytvoření uzly. XML modelu DOM (Document Object) má několik druhů typy uzlů, dáno World Wide Web Consortium (W3C) a uvedené v části 1.1.1 modelu DOM struktura. Následující tabulka uvádí typy uzlů přiřazené pro daný typ uzlu a krátký popis každého objektu.  
  
|Typ uzlu DOM|Objekt|Popis|  
|-------------------|------------|-----------------|  
|Dokument|<xref:System.Xml.XmlDocument>|Kontejner všechny uzly ve stromu. Je také označované jako kořen dokumentu, který není vždy stejná jako kořenový element.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Dočasné kontejner obsahující jeden nebo více uzlů bez jakékoli stromové struktury.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Představuje `<!DOCTYPE…>` uzlu.|  
|Třída EntityReference|<xref:System.Xml.XmlEntityReference>|Představuje text odkazu-rozšířit entity.|  
|Prvek|<xref:System.Xml.XmlElement>|Představuje uzel elementu.|  
|Line|<xref:System.Xml.XmlAttribute>|Je atribut elementu.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Je uzel zpracování instrukcí.|  
|Komentář|<xref:System.Xml.XmlComment>|Uzel komentáře.|  
|Text|<xref:System.Xml.XmlText>|Text, které patří do elementu nebo atributu.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Představuje CDATA.|  
|Entity|<xref:System.Xml.XmlEntity>|Představuje `<!ENTITY…>` deklarace ve formátu XML dokumentu z dokumentu interní typ definice (DTD) podmnožinu nebo z externí specifikace DTD a parametr entity.|  
|Zápis|<xref:System.Xml.XmlNotation>|Představuje notace deklarované v DTD.|  
  
 I když atribut (*line*), je uvedena v W3C DOM úrovně 1 části 1.2 základní rozhraní jako uzel, není to považováno za podřízený element uzlů.  
  
 Následující tabulka uvádí typy dalšího uzlu není definovaných pomocí W3C, ale jsou k dispozici pro použití v objektový model rozhraní Microsoft .NET Framework jako **XmlNodeType** výčty. Proto neexistuje odpovídající sloupec typu uzlu DOM pro tyto typy uzlů.  
  
|Typ uzlu|Popis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Představuje uzel deklarace `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Představuje významné prázdné znaky, které je prázdné místo v smíšený obsah.|  
|<xref:System.Xml.XmlWhitespace>|Představuje prázdné znaky v obsahu elementu.|  
|EndElement|Vrácená při **XmlReader** získá na konec elementu.<br /><br /> Příklad kódu XML:  **\< /bodu >**<br /><br /> Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Vrácená při **XmlReader** získá na konec nahrazení entity v důsledku volání <xref:System.Xml.XmlReader.ResolveEntity%2A>. Další informace naleznete v tématu <xref:System.Xml.XmlNodeType>.|  
  
 Pokud chcete zobrazit příklad kódu, který čte v kódu XML a používá případu konstrukce na typy uzlů na tiskové informace o uzlu a její obsah, najdete v části <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Další informace o hierarchie objektů typy uzlů a jejich název ekvivalentnímu objektu v tématu [hierarchii XML modelu DOM (Document Object)](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Další informace o objekty vytvořené v uzlu stromu najdete v tématu [mapování hierarchie objektů na XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
