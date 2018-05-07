---
title: 'Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 807a34ac50ea317ace42ec12eddcd9ec7cf3736b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front
Pomocí integrace vazby služby MSMQ pro převod MSMQ zprávy do a z zpráv WCF můžete integrovat existující aplikace služby Řízení front zpráv (MSMQ) s aplikacemi Windows Communication Foundation (WCF). To umožňuje provádět volání do aplikacím služby MSMQ příjemce od klientů WCF a také volání do služby WCF z aplikacím služby MSMQ odesílatele.  
  
 V této části vám vysvětlíme, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci mezi (1) klienta WCF a služby MSMQ aplikace napsané v System.Messaging a (2) k klientů služby MSMQ aplikace a služby WCF ve frontě.  
  
 Kompletní příklad, který ukazuje způsob volání služby MSMQ přijímající aplikace z klienta WCF, najdete v článku [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázka.  
  
 Kompletní příklad, který ukazuje způsob volání služby WCF z klienta služby MSMQ, najdete v článku [služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ukázka.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Vytvoření služby WCF, která přijímá zprávy od klientů služby MSMQ  
  
1.  Definujte rozhraní, které definuje kontrakt služby pro službu WCF, která přijímá zprávy ve frontě z aplikace služby MSMQ odesílatele, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Toto rozhraní implementovat a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut třídu, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Vytvoření konfiguračního souboru, který určuje <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Vytváření instancí <xref:System.ServiceModel.ServiceHost> objekt, který používá nakonfigurovanou vazbu.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Vytvoření klienta WCF, která odesílá zprávy k příjemce aplikaci služby MSMQ  
  
1.  Definujte rozhraní, které definuje kontrakt služby pro klienta WCF zasílá zařazených do fronty zpráv MSMQ příjemce, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Definice třídy klienta, která používá klienta WCF pro volání služby MSMQ příjemce.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  Vytvoření konfigurace, které určuje použití – MsmqIntegrationBinding vazby.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  Vytvoření instance třídy klienta a volejte metodu definované zpráva přijetí služby.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
