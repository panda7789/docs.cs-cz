---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 27402017e5e79194578719fd0c921dfc1e047b80
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512957"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="70b9f-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="70b9f-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="70b9f-103">Nezpracovatelná zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="70b9f-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="70b9f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="70b9f-104">Description</span></span>  
 <span data-ttu-id="70b9f-105">Trasování označuje, že nezpracovatelná zpráva byla došlo k a následně odmítnuto.</span><span class="sxs-lookup"><span data-stu-id="70b9f-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="70b9f-106">K tomu dojde při `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="70b9f-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="70b9f-107">Odmítnuté zprávy se doručí zpět do odesílatele [fronty nedoručených zpráv](https://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="70b9f-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="70b9f-108">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkId=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="70b9f-108">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="70b9f-109">Zobrazit [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) pro další podrobnosti o tom, co znamená odmítnuté zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="70b9f-109">See [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b9f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="70b9f-110">See Also</span></span>  
 [<span data-ttu-id="70b9f-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="70b9f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="70b9f-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="70b9f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="70b9f-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="70b9f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="70b9f-114">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="70b9f-114">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="70b9f-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="70b9f-115">MQMarkMessageRejected</span></span>](https://go.microsoft.com/fwlink/?LinkId=99548)
