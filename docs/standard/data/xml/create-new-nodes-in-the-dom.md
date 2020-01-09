---
title: Vytváření nových uzlů v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: f48990286405baee347becef87d0511cd42e9e77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710996"
---
# <a name="create-new-nodes-in-the-dom"></a>Vytváření nových uzlů v modelu DOM
<xref:System.Xml.XmlDocument> má metodu create pro všechny typy uzlů. Poskytněte metodu s názvem v případě potřeby a obsah nebo jiné parametry pro tyto uzly, které mají obsah (například textový uzel) a uzel je vytvořen. Níže jsou uvedené metody, které vyžadují název a několik dalších parametrů, které mají vytvořit vhodný uzel.  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Jiné typy uzlů mají více požadavků, než stačí poskytnout data parametrům.  
  
 Informace o atributech naleznete v tématu [vytváření nových atributů pro prvky v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Informace o ověřování prvků a názvů atributů naleznete v tématu [ověření názvu elementu XML a atributů při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Informace o vytváření odkazů na entity najdete v tématu [vytváření nových odkazů na entity](../../../../docs/standard/data/xml/creating-new-entity-references.md). Informace o tom, jak obory názvů ovlivňují rozšiřování odkazů na entity, najdete v tématu věnovaném [oboru názvů vliv na rozšíření odkazu na entity pro nové uzly obsahující prvky a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po vytvoření nových uzlů je k dispozici několik metod, které jsou k dispozici pro jejich vložení do stromu. V tabulce jsou uvedeny metody s popisem, kde se nový uzel zobrazuje v souboru XML model DOM (Document Object Model) (DOM).  
  
|Metoda|Umístění uzlu|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Vloženo před referenční uzel. Například pro vložení nového uzlu na pozici 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Další informace naleznete v metodě <xref:System.Xml.XmlNode.InsertBefore%2A>.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Vloženo za referenční uzel. Příklad:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Další informace naleznete v metodě <xref:System.Xml.XmlNode.InsertAfter%2A>.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Přidá uzel na konec seznamu podřízených uzlů pro daný uzel. Pokud je přidaný uzel <xref:System.Xml.XmlDocumentFragment>, celý obsah fragmentu dokumentu se přesune do podřízeného seznamu tohoto uzlu. Další informace naleznete v metodě <xref:System.Xml.XmlNode.AppendChild%2A>.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Přidá uzel na začátek seznamu podřízených uzlů daného uzlu. Pokud je přidaný uzel <xref:System.Xml.XmlDocumentFragment>, celý obsah fragmentu dokumentu se přesune do podřízeného seznamu tohoto uzlu. Další informace naleznete v metodě <xref:System.Xml.XmlNode.PrependChild%2A>.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Připojí uzel <xref:System.Xml.XmlAttribute> na konec kolekce atributů přidružené k elementu. Další informace naleznete v metodě <xref:System.Xml.XmlAttributeCollection.Append%2A>.|  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
