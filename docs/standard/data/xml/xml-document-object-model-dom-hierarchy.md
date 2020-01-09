---
title: Hierarchie modelu DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709969"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchie modelu DOM (Document Object Model) dokumentu XML
Následující ilustrace znázorňuje hierarchii tříd pro XML model DOM (Document Object Model) (DOM), s názvem konsorcium World Wide Web (W3C) v závorkách spolu s názvem třídy, kde je relevantní.  
  
 ![XML model DOM (Document Object Model) &#40;hierarchie&#41; DOM](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchie XML model DOM (Document Object Model) (DOM)  
  
 Následující třídy nedědí z **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 Třída **XmlImplementation** se používá k vytvoření dokumentu XML. Další informace najdete v tématu [vytváření dokumentů XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 Třída **XmlNamedNodeMap** zpracovává neuspořádanou sadu uzlů. Další informace naleznete v tématu [neuspořádané načtení uzlu podle názvu nebo indexu](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 Třída **XmlNodeList** zpracovává uspořádaný seznam uzlů. Další informace naleznete v tématu [pořadí načítání uzlů podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 Třída **XmlNodeChangedEventArgs** zpracovává obslužné rutiny událostí registrované v **XmlDocument**. Další informace naleznete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 Třída **XmlLinkedNode** dědí z typu **XmlNode**. Jeho účelem je přepsat dvě metody z **XmlNode**: metody **PreviousSibling** a **NextSibling** . Tyto přepsané metody jsou potom zděděné a používané v **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**a **XmlProcessingInstruction**, což jsou třídy, které mají předchozí a další na stejné úrovni.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
