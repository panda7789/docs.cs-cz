---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674802"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="937a8-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="937a8-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="937a8-103">Služba MSMQ zprávu vynechala.</span><span class="sxs-lookup"><span data-stu-id="937a8-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="937a8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="937a8-104">Description</span></span>  
 <span data-ttu-id="937a8-105">Trasování označuje, že zpráva služby MSMQ byla vynechána.</span><span class="sxs-lookup"><span data-stu-id="937a8-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="937a8-106">Zprávy služby MSMQ mohou být zrušeny, pokud je nelze zpracovat při službě WCF (wcf) systému Windows Communication Foundation (používané s vazací NetMsmqBinding nebo MsmqIntegrationBinding).</span><span class="sxs-lookup"><span data-stu-id="937a8-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="937a8-107">Tyto zprávy jsou označovány jako poškozená zprávy.</span><span class="sxs-lookup"><span data-stu-id="937a8-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="937a8-108">Poškozená zpráva je `ReceiveErrorHandling` vynechána, pokud je vlastnost na NetMsmqBinding `Drop`nebo MsmqIntegrationBinding nastavena na .</span><span class="sxs-lookup"><span data-stu-id="937a8-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="937a8-109">Vynechaná zpráva je odebrána z fronty a již není obnovitelná.</span><span class="sxs-lookup"><span data-stu-id="937a8-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="937a8-110">Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="937a8-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937a8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="937a8-111">See also</span></span>

- [<span data-ttu-id="937a8-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="937a8-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="937a8-113">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="937a8-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="937a8-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="937a8-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="937a8-115">Zpracování poškozená zpráva</span><span class="sxs-lookup"><span data-stu-id="937a8-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
