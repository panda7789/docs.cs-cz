---
title: "Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b18dab37a18723671cebf51c3cc943b907b38a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front
Můžete integrovat existující aplikace služby Řízení front zpráv (MSMQ) s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace pomocí integrace vazby služby MSMQ pro převod MSMQ zprávy do a z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy. To umožňuje provádět volání do aplikacím služby MSMQ příjemce z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, jakož i volání do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby od odesílatele aplikacím služby MSMQ.  
  
 V této části vám vysvětlíme, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci mezi ve frontě (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a služby MSMQ aplikace napsané v System.Messaging a (2) klienta aplikace služby MSMQ a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 Kompletní příklad, který ukazuje způsob volání služby MSMQ přijímající aplikace z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, najdete v článku [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázka.  
  
 Kompletní příklad, který ukazuje způsob volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ze služby MSMQ klienta najdete v tématu [služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ukázka.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Vytvoření služby WCF, která přijímá zprávy od klientů služby MSMQ  
  
1.  Definování rozhraní, které definuje kontrakt služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, která přijímá zprávy zařazené do fronty z aplikace služby MSMQ odesílatele, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Toto rozhraní implementovat a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut třídu, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Vytvoření konfiguračního souboru, který určuje <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Vytváření instancí <xref:System.ServiceModel.ServiceHost> objekt, který používá nakonfigurovanou vazbu.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Vytvoření klienta WCF, která odesílá zprávy k příjemce aplikaci služby MSMQ  
  
1.  Definování rozhraní, které definuje kontrakt služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který odešle zařazených do fronty zpráv k příjemce služby MSMQ, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Klienta definovat třídu, která [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient používá k volání služby MSMQ příjemce.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  Vytvoření konfigurace, které určuje použití – MsmqIntegrationBinding vazby.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  Vytvoření instance třídy klienta a volejte metodu definované zpráva přijetí služby.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také  
 [Fronty – přehled](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Postupy: výměna zpráv pomocí koncových bodů WCF zařazených do fronty.](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
