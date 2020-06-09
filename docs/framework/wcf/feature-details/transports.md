---
title: Přenosy ve službě Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598668"
---
# <a name="transports-in-windows-communication-foundation"></a>Přenosy ve službě Windows Communication Foundation
Transportní vrstva je na nejnižší úrovni zásobníku kanálů. Hlavní přenos používaný v Windows Communication Foundation (WCF) jsou HTTP, HTTPS, TCP a pojmenované kanály. Témata v této části popisují výběr mezi těmito přenosy, konfiguraci přenosu a nastavení vlastností optimalizace.  
  
 WCF zahrnuje další přenosy. Informace o přenosech služby Řízení front zpráv (označované také jako MSMQ) najdete v tématu [fronty a spolehlivé relace](queues-and-reliable-sessions.md). Informace o přenosu peer-to-peer najdete v tématu [sítě peer-](peer-to-peer-networking.md)to-peer.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba přenosu](choosing-a-transport.md)  
 V této části najdete popis tří hlavních přenosů a důležitých informací o výběru jedné z nich.  
  
 [Výběr kodéru zprávy](choosing-a-message-encoder.md)  
 Popisuje faktory, které je třeba zvážit při výběru prvku vazby s kódováním zpráv.  
  
 [Streamování přenosu zpráv](streaming-message-transfer.md)  
 V této části najdete popis postupu konfigurace přenosové vrstvy pro streamování.  
  
 [Konfigurace HTTP a HTTPS](configuring-http-and-https.md)  
 V této části najdete popis postupu konfigurace prvků vazby přenosu HTTP a HTTPS.  
  
 [Postupy: Nahrazení rezervace adresy URL služby WCF omezenou rezervací](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Popisuje, jak používat vyhrazené WCFURL rezervace.  
  
 [Přenosové kvóty](transport-quotas.md)  
 Popisuje okolnosti při nastavení kvót dostupných v transportní vrstvě.  
  
 [Práce s překlady adres (NAT) a bránami firewall](working-with-nats-and-firewalls.md)  
 V této části najdete popis postupu konfigurace přenosové vrstvy při posílání nebo přijímání zpráv za bránou firewall nebo při překladu síťových adres (NAT).  
  
 [Sdílení portů Net.TCP](net-tcp-port-sharing.md)  
 Popisuje, jak používat součást služby WCF pro sdílení portů Net. TCP.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Související oddíly  
 [Vazby](bindings.md)  
  
 [Rozšíření vazeb](../extending/extending-bindings.md)
