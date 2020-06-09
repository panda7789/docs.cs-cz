---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578048"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="dba1d-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="dba1d-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="dba1d-103">Služba MSMQ odmítla zprávu.</span><span class="sxs-lookup"><span data-stu-id="dba1d-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dba1d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="dba1d-104">Description</span></span>  
 <span data-ttu-id="dba1d-105">Toto trasování indikuje, že zpráva služby MSMQ byla odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="dba1d-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="dba1d-106">Zprávy služby MSMQ lze odmítat, pokud Windows Communication Foundation (WCF) (použité s NetMsmqBinding nebo MsmqIntegrationBinding) není schopen je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="dba1d-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="dba1d-107">Tyto zprávy se označují jako nepoškozené zprávy.</span><span class="sxs-lookup"><span data-stu-id="dba1d-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="dba1d-108">Pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na hodnotu, je nezpracovatelná zpráva odmítnuta `Reject` .</span><span class="sxs-lookup"><span data-stu-id="dba1d-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="dba1d-109">Odmítnutá zpráva se doručí zpátky do [fronty nedoručených](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)zpráv odesilatele.</span><span class="sxs-lookup"><span data-stu-id="dba1d-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="dba1d-110">Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="dba1d-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="dba1d-111">Další informace o tom, co odmítnutá zpráva znamená v MSMQ, najdete v tématu [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="dba1d-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba1d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="dba1d-112">See also</span></span>

- [<span data-ttu-id="dba1d-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="dba1d-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="dba1d-114">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="dba1d-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dba1d-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="dba1d-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="dba1d-116">Zpracování nezpracovatelných zpráv</span><span class="sxs-lookup"><span data-stu-id="dba1d-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="dba1d-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="dba1d-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>
