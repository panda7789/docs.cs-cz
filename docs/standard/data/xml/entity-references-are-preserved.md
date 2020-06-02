---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: e4c902df1b0cd2bd9e97b49c0ec1d10df91ef1c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290341"
---
# <a name="entity-references-are-preserved"></a>Odkazy na entity jsou zachované
Pokud odkaz na entitu není rozbalený, ale zachová, model DOM (Document Object Model) XML (DOM) vytvoří uzel **XmlEntityReference** , když dojde k odkazování na entitu.  
  
 Pomocí následujícího kódu XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 model DOM vytvoří uzel **XmlEntityReference** , když nalezne `&publisher;` odkaz. **XmlEntityReference** obsahuje podřízené uzly zkopírované z obsahu v deklaraci entity. Předchozí příklad kódu obsahuje text v deklaraci entity, takže se vytvoří uzel **XmlText** jako podřízený uzel uzlu odkazu na entitu.  
  
 ![Stromová struktura pro zachované odkazy na entity](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Stromová struktura pro Nezachované odkazy entit  
  
 Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořených z uzlu **XmlEntity** při zjištění deklarace entity.  
  
> [!NOTE]
> Uzly zkopírované z **XmlEntity** nejsou vždy přesně zkopírovány po umístění do uzlu odkaz na entitu. V uzlu odkazu na entitu můžou být obory názvů, které mají vliv na konečnou konfiguraci podřízených uzlů.  
  
 Ve výchozím nastavení jsou obecné entity jako `&abc;` zachované a **XmlEntityReference** uzly se vždycky vytvářejí.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
