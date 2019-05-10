---
title: Hierarchie modelu DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79078b16f0d56c40a3dcfeabaaed9b5cbb7753a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589826"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchie modelu DOM (Document Object Model) dokumentu XML
Následující obrázek znázorňuje hierarchii tříd pro XML Document Object Model (DOM), s World Wide Web Consortium (W3C) název v závorka spolu s názvem třídy, kde je to relevantní.  
  
 ![Modelu objektu dokumentu XML &#40;modelu DOM&#41; hierarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchie XML Document Object Model (DOM)  
  
 Následující třídy nedědí z **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** třída se používá k vytvoření dokumentu XML. Další informace najdete v tématu [vytváření dokumentů XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** třída zpracovává neuspořádanou sadu uzlů. Další informace najdete v tématu [Neseřazený načtení uzlů podle názvu nebo indexu](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** třída zpracovává uspořádaný seznam uzlů. Další informace najdete v tématu [seřazené načtení uzlů podle indexu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** třída zpracovává obslužné rutiny událostí zaregistrované na **XmlDocument**. Další informace najdete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** třída dědí z **XmlNode**. Jeho účelem je přepsat dvě metody ze **XmlNode**: **PreviousSibling** a **NextSibling** metody. Tyto přepsané metody jsou pak zděděné a používá **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, a **XmlProcessingInstruction**, které jsou třídy, které mají další a předchozí položky na stejné úrovni.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
