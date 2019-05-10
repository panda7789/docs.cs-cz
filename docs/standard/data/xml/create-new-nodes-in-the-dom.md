---
title: Vytváření nových uzlů v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59ac88b2e7c6b3ecd4d06c0183a2f8a7f4a9e2d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590255"
---
# <a name="create-new-nodes-in-the-dom"></a>Vytváření nových uzlů v modelu DOM
<xref:System.Xml.XmlDocument> Má vytvořit metodu pro všechny typy uzlů. Zadejte metodu s názvem v případě potřeby a obsah nebo jiné parametry pro ty uzly, které mají obsah (například textový uzel) a uzel se vytvoří. Jsou tyto metody těch, které je třeba název a několik dalších parametrů, které jsou vyplněny vytvořit příslušný uzel.  
  
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
  
 Jiné typy uzlů mají další požadavky než jenom poskytuje data pro parametry.  
  
 Informace o atributech naleznete v tématu [vytváření nových atributů pro elementy v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Informace o ověření názvu elementu a atribut, naleznete v tématu [– Element XML a ověření názvu atributu při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). K vytváření odkazů na entity, naleznete v tématu [vytváření odkazů na nové Entity](../../../../docs/standard/data/xml/creating-new-entity-references.md). Informace o vliv rozšíření odkazy na entity v oborech názvů najdete v tématu [Namespace vliv na rozšíření odkazu Entity pro nové uzly obsahující prvky a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po vytvoření nové uzly, existuje několik metod, které jsou k dispozici pro vložení do stromu. V tabulce jsou uvedeny metody s popisem toho, kde nového uzlu se zobrazuje v XML Document Object Model (DOM).  
  
|Metoda|Umístění uzlů|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Vložit před uzlu odkazu. Chcete-li například vložit nový uzel na pozici 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertBefore%2A> metody.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Vkládá uzlu odkazu. Příklad:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertAfter%2A> metody.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Uzel se přidá na konec seznamu podřízených uzlů pro daný uzel. Pokud uzel přidáván, je <xref:System.Xml.XmlDocumentFragment>, celý obsah část dokumentu přesunou do seznamu podřízených tohoto uzlu. Další informace najdete v tématu <xref:System.Xml.XmlNode.AppendChild%2A> metody.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Uzel se přidá na začátek seznamu podřízených uzlů daný uzel. Pokud uzel přidáván, je <xref:System.Xml.XmlDocumentFragment>, celý obsah část dokumentu přesunou do seznamu podřízených tohoto uzlu. Další informace najdete v tématu <xref:System.Xml.XmlNode.PrependChild%2A> metody.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Připojí <xref:System.Xml.XmlAttribute> uzlu na konec kolekce atributů spojených s elementem. Další informace najdete v tématu <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.|  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
