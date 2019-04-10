---
title: 'Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310301"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front
Stávající aplikace služby Řízení front zpráv (MSMQ) lze integrovat s aplikací Windows Communication Foundation (WCF) s využitím integrace vazby služby MSMQ pro převod MSMQ zprávy do a ze zprávy WCF. To umožňuje aplikacím služby MSMQ příjemce klientů WCF volat také volat vnořením služeb WCF z aplikace odesílatele služby MSMQ.  
  
 V této části vám vysvětlíme, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci mezi (1) klienta WCF a aplikací služby MSMQ napsané s využitím System.Messaging a (2) služby MSMQ aplikace klienta a služby WCF ve frontě.  
  
 Kompletní příklad, který ukazuje, jak volat služby MSMQ přijímající aplikace z klienta WCF, najdete v článku [Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) vzorku.  
  
 Kompletní příklad, který ukazuje, jak volat službu WCF z klienta služby MSMQ, najdete v článku [služby Řízení front zpráv do služby Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) vzorku.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Vytvoření služby WCF, která přijímá zprávy z klienta služby MSMQ  
  
1. Definujte rozhraní, který definuje kontrakt služby pro službu WCF, která přijímá zprávy ve frontě z aplikace odesílatele služby MSMQ, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Implementace rozhraní a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut pro třídu, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Vytvoření konfiguračního souboru, který určuje, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  

4. Vytvořit instanci <xref:System.ServiceModel.ServiceHost> objekt, který používá nakonfigurovanou vazbu.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>K vytvoření klienta WCF, která odesílá zprávy do přijímající aplikace služby MSMQ  
  
1. Definujte rozhraní, který definuje kontrakt služby pro klienta WCF, že odešle zprávy zařazené do fronty MSMQ příjemci, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Definujte třídu klienta, který používá klienta WCF pro volání služby MSMQ příjemce.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Vytvoření konfigurace, který určuje použití vazbu MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Vytvoření instance třídy klienta a volání metody definované ve zprávě přijetí služby.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Fronty – přehled](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Z WCF do Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Řízení front zpráv do WCF](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
