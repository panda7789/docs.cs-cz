---
title: Odkazy na entity se zachovají.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 652a044bf1b5293bc9c36477a46a78d9851f1810
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568482"
---
# <a name="entity-references-are-preserved"></a>Odkazy na entity se zachovají.
Pokud není odkaz na entitu rozšířit, ale je zachovaná, sestavení XML modelu DOM (Document Object) **XmlEntityReference** uzlu, pokud se setká s odkazu na entitu.  
  
 Pomocí následující kód XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 sestavení modelu DOM **XmlEntityReference** uzlu, když narazí `&publisher;` odkaz. **XmlEntityReference** obsahuje podřízené uzly zkopírovat z obsahu v deklaraci entity. V předchozím příkladu kódu obsahuje text v deklaraci entity, takže **XmlText** uzlu je vytvořen jako podřízený uzel entity uzlu odkazu.  
  
 ![Stromové struktury pro odkazy na zachované entity](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Stromovou strukturu pro odkazy na entity, které se zachovají  
  
 Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořené z **XmlEntity** uzlu deklarace entity došlo.  
  
> [!NOTE]
>  Uzly zkopírovaných z **XmlEntity** nejsou vždy přesné kopie jednou umístěn v uzlu odkazu entity. Může být obory názvů, které jsou v oboru v uzlu odkazu entity a která ovlivňuje finální konfiguraci podřízených uzlů.  
  
 Ve výchozím nastavení, jako například obecné entity `&abc;` zachovány a **XmlEntityReference** uzlů vždy vytvořené.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
