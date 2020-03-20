---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674815"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="c7b0c-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="c7b0c-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="c7b0c-103">Poškozená zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="c7b0c-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7b0c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c7b0c-104">Description</span></span>  

 <span data-ttu-id="c7b0c-105">Trasování označuje, že poškozená zpráva byla zjištěna a následně odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="c7b0c-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="c7b0c-106">K tomu dochází, `ReceiveErrorHandling` když je vlastnost na NetMsmqBinding nebo `Reject`MsmqIntegrationBinding nastavena na .</span><span class="sxs-lookup"><span data-stu-id="c7b0c-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="c7b0c-107">Odmítnutá zpráva je doručena zpět do [fronty nedoručených zpráv odesílatele](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span><span class="sxs-lookup"><span data-stu-id="c7b0c-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="c7b0c-108">Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="c7b0c-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="c7b0c-109">Další informace o tom, co znamená odmítnutá zpráva v msmq, naleznete v [tématu MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="c7b0c-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b0c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7b0c-110">See also</span></span>

- [<span data-ttu-id="c7b0c-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="c7b0c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c7b0c-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c7b0c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c7b0c-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="c7b0c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="c7b0c-114">Zpracování poškozená zpráva</span><span class="sxs-lookup"><span data-stu-id="c7b0c-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="c7b0c-115">[Zpráva MQMarkMessage byla odmítnuta.](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="c7b0c-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
