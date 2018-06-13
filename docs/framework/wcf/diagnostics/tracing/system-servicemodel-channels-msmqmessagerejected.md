---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478936"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="1b58d-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1b58d-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="1b58d-103">MSMQ odmítl zprávu.</span><span class="sxs-lookup"><span data-stu-id="1b58d-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1b58d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1b58d-104">Description</span></span>  
 <span data-ttu-id="1b58d-105">Trasování označuje, že služby MSMQ zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="1b58d-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="1b58d-106">Zprávy služby MSMQ může být odmítnutá při Windows Communication Foundation (WCF) (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="1b58d-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="1b58d-107">Takové zprávy se označují jako poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="1b58d-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="1b58d-108">Byl odmítnut nezpracovatelná zpráva při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="1b58d-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1b58d-109">Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="1b58d-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="1b58d-110">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="1b58d-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="1b58d-111">V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1b58d-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b58d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b58d-112">See Also</span></span>  
 [<span data-ttu-id="1b58d-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="1b58d-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1b58d-114">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="1b58d-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1b58d-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="1b58d-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="1b58d-116">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="1b58d-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="1b58d-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1b58d-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
