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
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="264f2-102">Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací pro řazení zpráv do front</span><span class="sxs-lookup"><span data-stu-id="264f2-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="264f2-103">Můžete integrovat existující aplikace služby Řízení front zpráv (MSMQ) s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace pomocí integrace vazby služby MSMQ pro převod MSMQ zprávy do a z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy.</span><span class="sxs-lookup"><span data-stu-id="264f2-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="264f2-104">To umožňuje provádět volání do aplikacím služby MSMQ příjemce z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, jakož i volání do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby od odesílatele aplikacím služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="264f2-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="264f2-105">V této části vám vysvětlíme, jak používat <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pro komunikaci mezi ve frontě (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta a služby MSMQ aplikace napsané v System.Messaging a (2) klienta aplikace služby MSMQ a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="264f2-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="264f2-106">Kompletní příklad, který ukazuje způsob volání služby MSMQ přijímající aplikace z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, najdete v článku [Windows Communication Foundation do řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="264f2-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="264f2-107">Kompletní příklad, který ukazuje způsob volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ze služby MSMQ klienta najdete v tématu [služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="264f2-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="264f2-108">Vytvoření služby WCF, která přijímá zprávy od klientů služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="264f2-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="264f2-109">Definování rozhraní, které definuje kontrakt služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, která přijímá zprávy zařazené do fronty z aplikace služby MSMQ odesílatele, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="264f2-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="264f2-110">Toto rozhraní implementovat a použít <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut třídu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="264f2-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="264f2-111">Vytvoření konfiguračního souboru, který určuje <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="264f2-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="264f2-112">Vytváření instancí <xref:System.ServiceModel.ServiceHost> objekt, který používá nakonfigurovanou vazbu.</span><span class="sxs-lookup"><span data-stu-id="264f2-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="264f2-113">Vytvoření klienta WCF, která odesílá zprávy k příjemce aplikaci služby MSMQ</span><span class="sxs-lookup"><span data-stu-id="264f2-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="264f2-114">Definování rozhraní, které definuje kontrakt služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který odešle zařazených do fronty zpráv k příjemce služby MSMQ, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="264f2-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="264f2-115">Klienta definovat třídu, která [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient používá k volání služby MSMQ příjemce.</span><span class="sxs-lookup"><span data-stu-id="264f2-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="264f2-116">Vytvoření konfigurace, které určuje použití – MsmqIntegrationBinding vazby.</span><span class="sxs-lookup"><span data-stu-id="264f2-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="264f2-117">Vytvoření instance třídy klienta a volejte metodu definované zpráva přijetí služby.</span><span class="sxs-lookup"><span data-stu-id="264f2-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="264f2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="264f2-118">See Also</span></span>  
 [<span data-ttu-id="264f2-119">Fronty – přehled</span><span class="sxs-lookup"><span data-stu-id="264f2-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="264f2-120">Postupy: výměna zpráv pomocí koncových bodů WCF zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="264f2-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="264f2-121">Windows Communication Foundation do řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="264f2-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="264f2-122">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="264f2-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="264f2-123">Řízení front zpráv do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="264f2-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="264f2-124">Zabezpečení zprávy pomocí služby Řízení front zpráv</span><span class="sxs-lookup"><span data-stu-id="264f2-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
