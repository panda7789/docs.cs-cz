---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674775"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="58d3f-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="58d3f-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="58d3f-103">Služba MSMQ zprávu odmítla.</span><span class="sxs-lookup"><span data-stu-id="58d3f-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="58d3f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="58d3f-104">Description</span></span>  
 <span data-ttu-id="58d3f-105">Toto trasování označuje, že zpráva služby MSMQ byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="58d3f-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="58d3f-106">Zprávy služby MSMQ lze odmítnout, pokud je nelze zpracovat při službě WCF (wcf) systému Windows Communication Foundation (používané s vazací NetMsmqBinding nebo MsmqIntegrationBinding).</span><span class="sxs-lookup"><span data-stu-id="58d3f-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="58d3f-107">Tyto zprávy jsou označovány jako poškozená zprávy.</span><span class="sxs-lookup"><span data-stu-id="58d3f-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="58d3f-108">Poškozená zpráva je `ReceiveErrorHandling` odmítnuta, pokud je vlastnost na NetMsmqBinding `Reject`nebo MsmqIntegrationBinding nastavena na .</span><span class="sxs-lookup"><span data-stu-id="58d3f-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="58d3f-109">Odmítnutá zpráva je doručena zpět do [fronty nedoručených zpráv odesílatele](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span><span class="sxs-lookup"><span data-stu-id="58d3f-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="58d3f-110">Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="58d3f-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="58d3f-111">Další informace o tom, co znamená odmítnutá zpráva v msmq, naleznete v [tématu MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="58d3f-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d3f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="58d3f-112">See also</span></span>

- [<span data-ttu-id="58d3f-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="58d3f-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="58d3f-114">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="58d3f-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="58d3f-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="58d3f-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="58d3f-116">Zpracování poškozená zpráva</span><span class="sxs-lookup"><span data-stu-id="58d3f-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="58d3f-117">[Zpráva MQMarkMessage byla odmítnuta.](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="58d3f-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
