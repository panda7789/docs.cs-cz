---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487903"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="c87ae-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="c87ae-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="c87ae-103">Nelze přesunout nebo zprávu odstranit.</span><span class="sxs-lookup"><span data-stu-id="c87ae-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c87ae-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c87ae-104">Description</span></span>  
 <span data-ttu-id="c87ae-105">Trasování označuje, že došlo k chybě při pokusu o přesunutí, odstraňte nebo odmítnout zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c87ae-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="c87ae-106">Zprávy služby MSMQ pracující ve Windows Communication Foundation (WCF) (při použití s – NetMsmqBinding nebo MsmqIntegrationBinding). Trasování se vztahuje k vybrané hodnotu `ReceiveErrorHandling` vlastnost na – NetMsmqBinding nebo – MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="c87ae-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="c87ae-107">Trasování není určující pro chybu celkové systému.</span><span class="sxs-lookup"><span data-stu-id="c87ae-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="c87ae-108">Však označuje, že zvolený škodlivých dispozice zpráva pro zprávu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="c87ae-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="c87ae-109">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="c87ae-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87ae-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c87ae-110">See Also</span></span>  
 [<span data-ttu-id="c87ae-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="c87ae-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c87ae-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c87ae-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c87ae-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="c87ae-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
