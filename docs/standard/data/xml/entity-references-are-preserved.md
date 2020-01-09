---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 0fd427388a065bd4c689d087c22fd6d69046b8a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710918"
---
# <a name="entity-references-are-preserved"></a>Odkazy na entity jsou zachované
Pokud odkaz na entitu není rozbalený, ale zachová, model DOM (Document Object Model) XML (DOM) vytvoří uzel **XmlEntityReference** , když dojde k odkazování na entitu.  
  
 Pomocí následujícího kódu XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 model DOM vytvoří uzel **XmlEntityReference** , když nalezne odkaz `&publisher;`. **XmlEntityReference** obsahuje podřízené uzly zkopírované z obsahu v deklaraci entity. Předchozí příklad kódu obsahuje text v deklaraci entity, takže se vytvoří uzel **XmlText** jako podřízený uzel uzlu odkazu na entitu.  
  
 ![Stromová struktura pro zachované odkazy na entity](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Stromová struktura pro Nezachované odkazy entit  
  
 Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořených z uzlu **XmlEntity** při zjištění deklarace entity.  
  
> [!NOTE]
> Uzly zkopírované z **XmlEntity** nejsou vždy přesně zkopírovány po umístění do uzlu odkaz na entitu. V uzlu odkazu na entitu můžou být obory názvů, které mají vliv na konečnou konfiguraci podřízených uzlů.  
  
 Ve výchozím nastavení jsou obecné entity jako `&abc;` zachované a uzly **XmlEntityReference** se vždy vytvoří.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
