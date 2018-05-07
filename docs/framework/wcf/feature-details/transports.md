---
title: Přenosy ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="transports-in-windows-communication-foundation"></a>Přenosy ve službě Windows Communication Foundation
Přenosová vrstva je na nejnižší úrovni kanálu zásobníku. Hlavní přenosy použít ve Windows Communication Foundation (WCF) jsou HTTP, HTTPS, TCP a pojmenované kanály. Témata v této části popisují výběru mezi tyto přenosy, konfigurace přenosu a nastavení, ladění vlastnosti.  
  
 WCF zahrnuje další přenosy. Informace o přenosu služby Řízení front zpráv (MSMQ) najdete v tématu [fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Informace o přenosu peer-to-peer najdete v tématu [Peer-to-Peer sítě](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Popisuje tři hlavní přenosy a zvolením některé aspekty.  
  
 [Výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Popisuje faktory, které je třeba zvážit při výběru element vazby kódování zprávy.  
  
 [Streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Popisuje postup konfigurace přenosové vrstvy udělat streamování.  
  
 [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Popisuje postup konfigurace elementů vazby přenosu HTTP a HTTPS.  
  
 [Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Popisuje, jak používat rezervace WCFURL omezený.  
  
 [Přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Popisuje důležité informace o nastavení kvóty, které jsou k dispozici v přenosové vrstvě.  
  
 [Práce s překlady adres (NAT) a bránami firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Popisuje postup konfigurace přenosové vrstvy, když jsou zprávy odesílané nebo přijímané za bránou firewall nebo když se nachází překlad síťových adres (NAT).  
  
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
