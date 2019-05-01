---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 562399c1d45dc73c7c88bd165e9f95ee1bcfa19d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997489"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="1e7d1-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1e7d1-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="1e7d1-103">Nezpracovatelná zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="1e7d1-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e7d1-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1e7d1-104">Description</span></span>  
 <span data-ttu-id="1e7d1-105">Trasování označuje, že nezpracovatelná zpráva byla došlo k a následně odmítnuto.</span><span class="sxs-lookup"><span data-stu-id="1e7d1-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="1e7d1-106">K tomu dojde při `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="1e7d1-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="1e7d1-107">Odmítnuté zprávy se doručí zpět do odesílatele [fronty nedoručených zpráv](https://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="1e7d1-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="1e7d1-108">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkId=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="1e7d1-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="1e7d1-109">Zobrazit [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) pro další podrobnosti o tom, co znamená odmítnuté zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1e7d1-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e7d1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e7d1-110">See also</span></span>

- [<span data-ttu-id="1e7d1-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="1e7d1-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1e7d1-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="1e7d1-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1e7d1-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="1e7d1-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="1e7d1-114">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="1e7d1-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)
- [<span data-ttu-id="1e7d1-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="1e7d1-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
