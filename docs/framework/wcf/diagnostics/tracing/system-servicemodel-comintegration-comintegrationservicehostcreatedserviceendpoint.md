---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="e66c9-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="e66c9-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="e66c9-103">Nelze přesunout nebo zprávu odstranit.</span><span class="sxs-lookup"><span data-stu-id="e66c9-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e66c9-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e66c9-104">Description</span></span>  
 <span data-ttu-id="e66c9-105">Trasování označuje, že došlo k chybě při pokusu o přesunutí, odstraňte nebo odmítnout zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e66c9-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="e66c9-106">Zaměstnává zpráv MSMQ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (při použití s – NetMsmqBinding nebo MsmqIntegrationBinding). Trasování se vztahuje k vybrané hodnotu `ReceiveErrorHandling` vlastnost na – NetMsmqBinding nebo – MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="e66c9-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="e66c9-107">Trasování není určující pro chybu celkové systému.</span><span class="sxs-lookup"><span data-stu-id="e66c9-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="e66c9-108">Však označuje, že zvolený škodlivých dispozice zpráva pro zprávu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e66c9-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="e66c9-109">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="e66c9-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66c9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e66c9-110">See Also</span></span>  
 [<span data-ttu-id="e66c9-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="e66c9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e66c9-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e66c9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e66c9-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e66c9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
