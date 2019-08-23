---
title: Kódování zpráv
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 8e5a71095ba62e0e2e6592c8b7b83b67602ef7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931596"
---
# <a name="message-encoding"></a>Kódování zpráv
Kódování je proces transformace sady znaků Unicode na sekvenci bajtů. Dekódování je zpětný proces. Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).  
  
 `binaryMessageEncoding` Konfigurační oddíl určuje kódování znaků a verze zprávy používané pro binární zprávy XML. Kodér binární zprávy kóduje Windows Communication Foundation (WCF) v binárním souboru na lince. I když toto kódování vede k velmi rychlému přenosu zpráv, vzájemná funkční spolupráce založená na standardech WS-* bude ztracena.  
  
 `mtomMessageEncoding` Konfigurační oddíl určuje kódování znaků a správu verzí zpráv, které se používají pro zprávu pomocí kódování MTOM (Message reoptimization mechanism). (MTOM) je efektivní technologie pro přenos binárních dat ve zprávách Windows Communication Foundation (WCF). Kodér MTOM se pokusí přeškrtnout rovnováhu mezi efektivitou a interoperabilitou. Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich přenosem tak, jak jsou, bez konverze na text.  
  
 `textMessageEncoding` Konfigurační oddíl určuje textový kodér, který slouží k vytváření textových zpráv na lince. Zprávy vytvářené v tomto kodéru jsou vhodné pro interoperabilitu WS-*. Webové služby nebo klient webové služby můžou obecně pochopit text XML. Nicméně přenos velkých bloků binárních dat jako textu je nejefektivnější metodou pro kódování zpráv XML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Výběr kodéru zprávy](../../../wcf/feature-details/choosing-a-message-encoder.md)
