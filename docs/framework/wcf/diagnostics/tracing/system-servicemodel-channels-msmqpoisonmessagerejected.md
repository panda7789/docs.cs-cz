---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55ae2ed6ac8a02218fa4c13063fb8b8a8c474fd8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="f2341-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f2341-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="f2341-103">Poškozená zpráva byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="f2341-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f2341-104">Popis</span><span class="sxs-lookup"><span data-stu-id="f2341-104">Description</span></span>  
 <span data-ttu-id="f2341-105">Trasování označuje, že byl nezpracovatelná zpráva došlo a následně odmítnuto.</span><span class="sxs-lookup"><span data-stu-id="f2341-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="f2341-106">K tomu dojde při `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Reject`.</span><span class="sxs-lookup"><span data-stu-id="f2341-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="f2341-107">Odmítnuté zprávy doručuje zpět do odesílatele [frontu nedoručených zpráv](http://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="f2341-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="f2341-108">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkId=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f2341-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="f2341-109">V tématu [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) další podrobnosti o odmítnuté zprávy znamená služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f2341-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2341-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2341-110">See Also</span></span>  
 [<span data-ttu-id="f2341-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="f2341-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f2341-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="f2341-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f2341-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="f2341-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="f2341-114">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="f2341-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="f2341-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f2341-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
