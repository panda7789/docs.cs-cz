---
title: Hierarchie modelu DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: a6099b6c5e30fbf2e4d5d4ed046369bc8f884845
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291432"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchie modelu DOM (Document Object Model) dokumentu XML
Následující ilustrace znázorňuje hierarchii tříd pro XML model DOM (Document Object Model) (DOM), s názvem konsorcium World Wide Web (W3C) v závorkách spolu s názvem třídy, kde je relevantní.  
  
 ![Hierarchie&#41; &#40;DOM model DOM (Document Object Model) XML](media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchie XML model DOM (Document Object Model) (DOM)  
  
 Následující třídy nedědí z **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 Třída **XmlImplementation** se používá k vytvoření dokumentu XML. Další informace najdete v tématu [vytváření dokumentů XML](xml-document-creation.md).  
  
 Třída **XmlNamedNodeMap** zpracovává neuspořádanou sadu uzlů. Další informace naleznete v tématu [neuspořádané načtení uzlu podle názvu nebo indexu](unordered-node-retrieval-by-name-or-index.md).  
  
 Třída **XmlNodeList** zpracovává uspořádaný seznam uzlů. Další informace naleznete v tématu [pořadí načítání uzlů podle indexu](ordered-node-retrieval-by-index.md).  
  
 Třída **XmlNodeChangedEventArgs** zpracovává obslužné rutiny událostí registrované v **XmlDocument**. Další informace naleznete v tématu [zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 Třída **XmlLinkedNode** dědí z typu **XmlNode**. Jeho účelem je přepsat dvě metody z **XmlNode**: metody **PreviousSibling** a **NextSibling** . Tyto přepsané metody jsou potom zděděné a používané v **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**a **XmlProcessingInstruction**, což jsou třídy, které mají předchozí a další na stejné úrovni.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
