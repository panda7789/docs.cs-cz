---
title: "Přenosy ve službě Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9275f1812111365ed6b0fb3be6957cd9ca883fdf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Přenosy ve službě Windows Communication Foundation
Přenosová vrstva je na nejnižší úrovni kanálu zásobníku. Hlavní přenosy použít v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jsou HTTP, HTTPS, TCP a pojmenované kanály. Témata v této části popisují výběru mezi tyto přenosy, konfigurace přenosu a nastavení, ladění vlastnosti.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zahrnuje další přenosy. Informace o přenosu služby Řízení front zpráv (MSMQ) najdete v tématu [fronty a spolehlivé relace](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Informace o přenosu peer-to-peer najdete v tématu [Peer-to-Peer sítě](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Popisuje tři hlavní přenosy a zvolením některé aspekty.  
  
 [Výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Popisuje faktory, které je třeba zvážit při výběru element vazby kódování zprávy.  
  
 [Streamování přenosu zpráv](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Popisuje postup konfigurace přenosové vrstvy udělat streamování.  
  
 [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Popisuje postup konfigurace elementů vazby přenosu HTTP a HTTPS.  
  
 [Postupy: nahrazení rezervace adresy URL WCF omezenou rezervací](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Popisuje způsob použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]omezený rezervace adresy URL.  
  
 [Přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Popisuje důležité informace o nastavení kvóty, které jsou k dispozici v přenosové vrstvě.  
  
 [Práce se zařízeními NAT a brány firewall](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Popisuje postup konfigurace přenosové vrstvy, když jsou zprávy odesílané nebo přijímané za bránou firewall nebo když se nachází překlad síťových adres (NAT).  
  
 [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Popisuje postup používání sdílení portů Net.TCP komponenta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Související oddíly  
 [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Rozšiřování vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
