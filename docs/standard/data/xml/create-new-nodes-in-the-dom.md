---
title: Vytvořit nové uzly v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="create-new-nodes-in-the-dom"></a>Vytvořit nové uzly v modelu DOM
<xref:System.Xml.XmlDocument> Má metodu create pro všechny typy uzlů. Zadejte metodu s názvem vyžádání a obsah nebo jiné parametry pro uzly, u kterých se obsah (například textový uzel) a uzlu je vytvořena. Tyto metody jsou ty, které je třeba název a několik dalších parametrů, které jsou vyplněna můžete vytvořit příslušný uzel.  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Ostatní typy uzlů mají další požadavky než právě poskytuje data na parametry.  
  
 Informace o atributech, najdete v části [vytváření nové atributy pro elementy v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Informace o ověření názvu elementu a atributu v tématu [– Element XML a ověření názvu atributu při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Vytváření odkazy na entity, najdete v části [vytváření nové odkazy na Entity](../../../../docs/standard/data/xml/creating-new-entity-references.md). Informace o vlivu rozšíření odkazy na entity obory názvů, v tématu [Namespace vlivu na Entity odkaz na rozšíření pro nové uzly obsahující elementy a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po vytvoření nové uzly jsou existuje několik metod, které jsou k dispozici pro vložte je do stromu. Tabulka uvádí metody popisem toho, kde se nový uzel objeví v XML dokumentu objektu modelu (DOM).  
  
|Metoda|Umístění uzlu|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Vložit před uzlu odkazu. Chcete-li například vložit nový uzel v pozici 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertBefore%2A> metoda.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Vložit po uzlu odkazu. Příklad:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertAfter%2A> metoda.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Přidá na konec seznamu podřízené uzly pro daný uzel uzlu. Pokud uzel, který chcete přidat je <xref:System.Xml.XmlDocumentFragment>, celý obsah dokumentu fragment přesunou do seznamu podřízené tohoto uzlu. Další informace najdete v tématu <xref:System.Xml.XmlNode.AppendChild%2A> metoda.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Přidá na začátek seznamu podřízené uzly uzlu daného uzlu. Pokud uzel, který chcete přidat je <xref:System.Xml.XmlDocumentFragment>, celý obsah dokumentu fragment přesunou do seznamu podřízené tohoto uzlu. Další informace najdete v tématu <xref:System.Xml.XmlNode.PrependChild%2A> metoda.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Připojí <xref:System.Xml.XmlAttribute> uzlu na konec kolekce atributů, které jsou spojené s elementem. Další informace najdete v tématu <xref:System.Xml.XmlAttributeCollection.Append%2A> metoda.|  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
