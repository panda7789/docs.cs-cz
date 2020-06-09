---
title: 'Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0775de90903aed27a8d0006614a4b6f2d857eee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597095"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front
Stávající aplikace služby Řízení front zpráv (MSMQ) s aplikacemi Windows Communication Foundation (WCF) můžete integrovat pomocí vazby integrace služby MSMQ k převodu zpráv služby MSMQ do a ze zpráv WCF. Díky tomu můžete volat aplikace přijímače MSMQ od klientů WCF a volat služby WCF z aplikací odesílatele MSMQ.  
  
 V této části vysvětlete, jak použít <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci ve frontě mezi (1) klientem WCF a aplikační službou MSMQ napsanou pomocí System. Messaging a (2) klient aplikace služby MSMQ a služba WCF.  
  
 Úplný příklad, který ukazuje, jak zavolat aplikaci příjemce služby MSMQ z klienta WCF, naleznete v tématu Ukázka [služby Řízení front zpráv v Windows Communication Foundation](../samples/wcf-to-message-queuing.md) .  
  
 Úplný příklad, který ukazuje, jak volat službu WCF z klienta služby MSMQ, najdete v tématu Ukázka [Řízení front zpráv do Windows Communication Foundation](../samples/message-queuing-to-wcf.md) .  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Vytvoření služby WCF, která přijímá zprávy z klienta služby MSMQ  
  
1. Definujte rozhraní, které definuje kontrakt služby pro službu WCF, která přijímá zprávy ve frontě z aplikace odesílatele služby MSMQ, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Implementujte rozhraní a použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut pro třídu, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Vytvořte konfigurační soubor, který určuje <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .  

4. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> objektu, který používá nakonfigurovanou vazbu.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Vytvoření klienta WCF odesílajícího zprávy do aplikace příjemce služby MSMQ  
  
1. Definujte rozhraní, které definuje kontrakt služby pro klienta WCF odesílající zprávy zařazené do fronty na příjemce služby MSMQ, jak je znázorněno v následujícím příkladu kódu.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Definujte třídu klienta, kterou klient služby WCF používá pro volání přijímače MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Vytvořte konfiguraci, která určuje použití vazby MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Vytvořte instanci klientské třídy a zavolejte metodu definovanou službou přijímání zpráv.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Viz také

- [Přehled front](queues-overview.md)
- [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Z WCF do Řízení front zpráv](../samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Řízení front zpráv do WCF](../samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../samples/message-security-over-message-queuing.md)
