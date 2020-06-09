---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598369"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="4cf94-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="4cf94-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="4cf94-103">Nezpracovatelná zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="4cf94-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4cf94-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4cf94-104">Description</span></span>  

 <span data-ttu-id="4cf94-105">Trasování indikuje, že byla zjištěna nezpracovatelná zpráva a následně zamítnuta.</span><span class="sxs-lookup"><span data-stu-id="4cf94-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="4cf94-106">K tomu dochází, pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na `Reject` .</span><span class="sxs-lookup"><span data-stu-id="4cf94-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="4cf94-107">Odmítnutá zpráva se doručí zpátky do [fronty nedoručených](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)zpráv odesilatele.</span><span class="sxs-lookup"><span data-stu-id="4cf94-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="4cf94-108">Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="4cf94-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="4cf94-109">Další informace o tom, co odmítnutá zpráva znamená v MSMQ, najdete v tématu [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="4cf94-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf94-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cf94-110">See also</span></span>

- [<span data-ttu-id="4cf94-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="4cf94-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="4cf94-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="4cf94-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4cf94-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="4cf94-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="4cf94-114">Zpracování nezpracovatelných zpráv</span><span class="sxs-lookup"><span data-stu-id="4cf94-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="4cf94-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="4cf94-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
