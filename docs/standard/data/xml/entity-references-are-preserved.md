---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934525"
---
# <a name="entity-references-are-preserved"></a>Odkazy na entity jsou zachované
Pokud odkaz na entitu není rozbalen, ale zachovají, sestavení XML Document Object Model (DOM) **XmlEntityReference** uzlu, pokud se setká s odkazu na entitu.  
  
 Pomocí následující kód XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 sestavení modelu DOM **XmlEntityReference** uzlu, pokud se setká `&publisher;` odkaz. **XmlEntityReference** obsahuje podřízené uzly, které jsou kopírovány z obsahu entity prohlášení. Předchozí příklad kódu obsahuje text v entity prohlášení, takže **XmlText** uzel je vytvořen jako podřízený uzel uzlu odkazu entity.  
  
 ![Stromová struktura pro odkazy na entity zachovaných](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Stromovou strukturu pro odkazy na entity, které jsou zachovány  
  
 Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořené z **XmlEntity** uzlu, když došlo k deklaraci entity.  
  
> [!NOTE]
>  Uzly zkopírovanými z **XmlEntity** nejsou vždy přesné kopie jednou umístit odkaz uzlu entity. Může být obory názvů, které jsou v rozsahu v uzlu odkazu entity a, který má vliv na konečnou konfiguraci podřízené uzly.  
  
 Ve výchozím nastavení, jako jsou obecné entity `&abc;` jsou zachovány a **XmlEntityReference** vždy vytvoří uzly.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
