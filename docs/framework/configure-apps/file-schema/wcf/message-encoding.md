---
title: Kódování zpráv
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: cdfa83b722492a8b2a7b118ff70134916ed824fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752491"
---
# <a name="message-encoding"></a>Kódování zpráv
Proces transformace sadu znaků Unicode do pořadí bajtů kódování je. Dekódování je zpětné proces. Windows Communication Foundation (WCF) zahrnuje tři typy kódování pro protokolu SOAP zprávy: Text, Binary a zpráva přenosu optimalizace mechanismus (MTOM).  
  
 `binaryMessageEncoding` Znak kódování a zpráva verze založené na binární soubor XML pro zprávy určuje konfigurační oddíl. Kodér zprávy v binární kódování zpráv Windows Communication Foundation (WCF) v binárním v drátové síti. Když toto kódování výsledkem velmi rychlé přenos zpráv, interoperabilita založené na protokolu WS-* dojde ke ztrátě standardů.  
  
 `mtomMessageEncoding` Konfigurační oddíl Určuje kódování a zpráva verze znak použít pro zprávu pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM). (MTOM) je technologie efektivní přenosu zpráv binární data ve zprávách služby Windows Communication Foundation (WCF). Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převodu na text.  
  
 `textMessageEncoding` Konfigurační oddíl určuje kodér textu, používá k vytvoření textových zpráv v drátové síti. Zprávy vyprodukované tento kodér jsou vhodné pro WS-* na základě zprostředkovatel komunikace s objekty. Webová služba nebo klient webové služby lze obecně pochopit textovou XML. Přenos velkých bloků binárních dat jako text je však alespoň efektivní metodu pro kódování zpráv XML  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
