---
title: Integrace služby Řízení front zpráv
ms.date: 03/30/2017
ms.assetid: 8d2b47a0-5d51-45b5-9633-b62e064e8ea4
ms.openlocfilehash: 5c1f41c97148782a83c6b11dd60b808cfe8b2b34
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="message-queueing-integration"></a>Integrace služby Řízení front zpráv
Tato část obsahuje příklady vysvětlující integrace mezi služby Řízení front zpráv a Windows Communication Foundation (WCF).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 Ukazuje, jak můžete k aplikaci služby Řízení front zpráv (MSMQ) odešle zprávu MSMQ do služby WCF.  
  
 [Vlastní demux](../../../../docs/framework/wcf/samples/custom-demux.md)  
 Ukazuje, jak hlavičky zpráv MSMQ lze mapovat na jinou službu operations tak, aby služeb WCF, které používají <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nejsou omezeny na použití jedné operace služby.  
  
 [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 Ukazuje, jak aplikace WCF odeslat zprávu do aplikace služby Řízení front zpráv (MSMQ).  
  
 [Korelace zprávy](../../../../docs/framework/wcf/samples/message-correlation.md)  
 Ukazuje, jak služby Řízení front zpráv (MSMQ) aplikace může odesílat zprávy MSMQ na službu WCF a korelace zpráv mezi aplikacemi odesílatele a příjemce v případě požadavků a odpovědí.
