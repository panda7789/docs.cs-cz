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
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="d7bb9-102">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="d7bb9-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="d7bb9-103">Stávající aplikace služby Řízení front zpráv (MSMQ) s aplikacemi Windows Communication Foundation (WCF) můžete integrovat pomocí vazby integrace služby MSMQ k převodu zpráv služby MSMQ do a ze zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="d7bb9-104">Díky tomu můžete volat aplikace přijímače MSMQ od klientů WCF a volat služby WCF z aplikací odesílatele MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="d7bb9-105">V této části vysvětlete, jak použít <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci ve frontě mezi (1) klientem WCF a aplikační službou MSMQ napsanou pomocí System. Messaging a (2) klient aplikace služby MSMQ a služba WCF.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="d7bb9-106">Úplný příklad, který ukazuje, jak zavolat aplikaci příjemce služby MSMQ z klienta WCF, naleznete v tématu Ukázka [služby Řízení front zpráv v Windows Communication Foundation](../samples/wcf-to-message-queuing.md) .</span><span class="sxs-lookup"><span data-stu-id="d7bb9-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="d7bb9-107">Úplný příklad, který ukazuje, jak volat službu WCF z klienta služby MSMQ, najdete v tématu Ukázka [Řízení front zpráv do Windows Communication Foundation](../samples/message-queuing-to-wcf.md) .</span><span class="sxs-lookup"><span data-stu-id="d7bb9-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="d7bb9-108">Vytvoření služby WCF, která přijímá zprávy z klienta služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="d7bb9-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="d7bb9-109">Definujte rozhraní, které definuje kontrakt služby pro službu WCF, která přijímá zprávy ve frontě z aplikace odesílatele služby MSMQ, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="d7bb9-110">Implementujte rozhraní a použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut pro třídu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="d7bb9-111">Vytvořte konfigurační soubor, který určuje <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .</span><span class="sxs-lookup"><span data-stu-id="d7bb9-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="d7bb9-112">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> objektu, který používá nakonfigurovanou vazbu.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="d7bb9-113">Vytvoření klienta WCF odesílajícího zprávy do aplikace příjemce služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="d7bb9-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="d7bb9-114">Definujte rozhraní, které definuje kontrakt služby pro klienta WCF odesílající zprávy zařazené do fronty na příjemce služby MSMQ, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="d7bb9-115">Definujte třídu klienta, kterou klient služby WCF používá pro volání přijímače MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="d7bb9-116">Vytvořte konfiguraci, která určuje použití vazby MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="d7bb9-117">Vytvořte instanci klientské třídy a zavolejte metodu definovanou službou přijímání zpráv.</span><span class="sxs-lookup"><span data-stu-id="d7bb9-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d7bb9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7bb9-118">See also</span></span>

- [<span data-ttu-id="d7bb9-119">Přehled front</span><span class="sxs-lookup"><span data-stu-id="d7bb9-119">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="d7bb9-120">Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF</span><span class="sxs-lookup"><span data-stu-id="d7bb9-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="d7bb9-121">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="d7bb9-121">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="d7bb9-122">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="d7bb9-122">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="d7bb9-123">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="d7bb9-123">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="d7bb9-124">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="d7bb9-124">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
