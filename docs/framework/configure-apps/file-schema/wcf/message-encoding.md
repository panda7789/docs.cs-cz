---
title: Kódování zpráv
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 7fb0d4a994eaf1497841691eb76261329a48599d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168750"
---
# <a name="message-encoding"></a>Kódování zpráv
Kódování je proces transformace sady znaků Unicode na sekvenci bajtů. Dekódování je opačný proces. Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a mechanismus optimalizaci přenosu zprávu (MTOM).  
  
 `binaryMessageEncoding` Konfigurační oddíl určuje na znak kódování a správu verzí zpráv použít pro binární soubor založené zprávy XML. Kodér binárních zpráv kóduje zprávy služby Windows Communication Foundation (WCF) v binárním souboru na lince. Když toto kódování má za následek velmi rychlé zpracování přenos zpráv, vzájemná funkční spolupráce podle WS-* standardů se ztratí.  
  
 `mtomMessageEncoding` Konfigurační oddíl určuje na znak kódování a správu verzí zpráv používá zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM). (MTOM) je efektivní technologie pro přenos binární data v zpráv Windows Communication Foundation (WCF). Kodér MTOM se pokusí hledají rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na text.  
  
 `textMessageEncoding` Kodér textu použitý k vytvoření textových zpráv na lince Určuje konfigurační oddíl. Zprávy vytvořené v tomto kodéru jsou vhodné pro WS-* na základě spolupráce. Webová služba nebo klient webové služby obecně by rozuměla textové XML. Přenášení velkých bloků binárních dat jako text je však nejméně efektivní způsob pro kódování zpráv XML  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
