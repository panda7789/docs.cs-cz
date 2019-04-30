---
title: Přenosy ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933728"
---
# <a name="transports-in-windows-communication-foundation"></a>Přenosy ve službě Windows Communication Foundation
Přenosové vrstvy je na nejnižší úrovni zásobníku kanálu. Hlavní přenosy použít ve Windows Communication Foundation (WCF) jsou HTTP, HTTPS, TCP a pojmenované kanály. Témata v této části popisují výběru mezi tyto přenosy, přenos konfigurace a nastavení vlastnosti optimalizace.  
  
 WCF obsahuje další přenosy. Informace o přenosu služby Řízení front zpráv (MSMQ) najdete v tématu [fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Informace o přenosu peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Popisuje tři hlavní přenosy a důležité informace při výběru jednoho.  
  
 [Výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Popisuje faktory, které je třeba zvážit při výběru element vazby kódování zprávy.  
  
 [Streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Popisuje postup konfigurace přenosové vrstvy provedete streamování.  
  
 [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Popisuje postup konfigurace elementů vazby přenosu HTTP a HTTPS.  
  
 [Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Popisuje, jak používat s omezením pomocí specifikátoru WCFURL rezervace.  
  
 [Přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Popisuje důležité informace v nastavení kvót, které jsou k dispozici v přenosové vrstvě.  
  
 [Práce s překlady adres (NAT) a bránami firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Popisuje postup konfigurace přenosové vrstvy, když se zprávy odesílané nebo přijímané za bránou firewall nebo překlad síťových adres (NAT) je k dispozici.  
  
 [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Popisuje postup používání sdílení portů Net.TCP komponent služby WCF.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Související oddíly  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
