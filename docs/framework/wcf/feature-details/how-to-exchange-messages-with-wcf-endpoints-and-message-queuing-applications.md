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
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="64b31-102">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="64b31-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="64b31-103">Stávající aplikace služby Řízení front zpráv (MSMQ) lze integrovat s aplikací Windows Communication Foundation (WCF) s využitím integrace vazby služby MSMQ pro převod MSMQ zprávy do a ze zprávy WCF.</span><span class="sxs-lookup"><span data-stu-id="64b31-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="64b31-104">To umožňuje aplikacím služby MSMQ příjemce klientů WCF volat také volat vnořením služeb WCF z aplikace odesílatele služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="64b31-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="64b31-105">V této části vám vysvětlíme, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci mezi (1) klienta WCF a aplikací služby MSMQ napsané s využitím System.Messaging a (2) služby MSMQ aplikace klienta a služby WCF ve frontě.</span><span class="sxs-lookup"><span data-stu-id="64b31-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="64b31-106">Kompletní příklad, který ukazuje, jak volat služby MSMQ přijímající aplikace z klienta WCF, najdete v článku [Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="64b31-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="64b31-107">Kompletní příklad, který ukazuje, jak volat službu WCF z klienta služby MSMQ, najdete v článku [služby Řízení front zpráv do služby Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="64b31-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="64b31-108">Vytvoření služby WCF, která přijímá zprávy z klienta služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="64b31-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="64b31-109">Definujte rozhraní, který definuje kontrakt služby pro službu WCF, která přijímá zprávy ve frontě z aplikace odesílatele služby MSMQ, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="64b31-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="64b31-110">Implementace rozhraní a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut pro třídu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="64b31-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="64b31-111">Vytvoření konfiguračního souboru, který určuje, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="64b31-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="64b31-112">Vytvořit instanci <xref:System.ServiceModel.ServiceHost> objekt, který používá nakonfigurovanou vazbu.</span><span class="sxs-lookup"><span data-stu-id="64b31-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="64b31-113">K vytvoření klienta WCF, která odesílá zprávy do přijímající aplikace služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="64b31-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="64b31-114">Definujte rozhraní, který definuje kontrakt služby pro klienta WCF, že odešle zprávy zařazené do fronty MSMQ příjemci, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="64b31-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="64b31-115">Definujte třídu klienta, který používá klienta WCF pro volání služby MSMQ příjemce.</span><span class="sxs-lookup"><span data-stu-id="64b31-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="64b31-116">Vytvoření konfigurace, který určuje použití vazbu MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="64b31-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="64b31-117">Vytvoření instance třídy klienta a volání metody definované ve zprávě přijetí služby.</span><span class="sxs-lookup"><span data-stu-id="64b31-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="64b31-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64b31-118">See also</span></span>

- [<span data-ttu-id="64b31-119">Fronty – přehled</span><span class="sxs-lookup"><span data-stu-id="64b31-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [<span data-ttu-id="64b31-120">Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF</span><span class="sxs-lookup"><span data-stu-id="64b31-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="64b31-121">Z WCF do Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="64b31-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="64b31-122">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="64b31-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="64b31-123">Řízení front zpráv do WCF</span><span class="sxs-lookup"><span data-stu-id="64b31-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="64b31-124">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="64b31-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
