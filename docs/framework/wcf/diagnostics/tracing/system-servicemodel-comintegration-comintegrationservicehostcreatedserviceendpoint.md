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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4cecacdcc9ec1155fbb374bb763f6858da6ccc57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="ee311-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="ee311-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="ee311-103">Nelze přesunout nebo zprávu odstranit.</span><span class="sxs-lookup"><span data-stu-id="ee311-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ee311-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ee311-104">Description</span></span>  
 <span data-ttu-id="ee311-105">Trasování označuje, že došlo k chybě při pokusu o přesunutí, odstraňte nebo odmítnout zprávu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ee311-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="ee311-106">Zaměstnává zpráv MSMQ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (při použití s – NetMsmqBinding nebo MsmqIntegrationBinding). Trasování se vztahuje k vybrané hodnotu `ReceiveErrorHandling` vlastnost na – NetMsmqBinding nebo – MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="ee311-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="ee311-107">Trasování není určující pro chybu celkové systému.</span><span class="sxs-lookup"><span data-stu-id="ee311-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="ee311-108">Však označuje, že zvolený škodlivých dispozice zpráva pro zprávu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ee311-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="ee311-109">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ee311-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee311-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee311-110">See Also</span></span>  
 [<span data-ttu-id="ee311-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="ee311-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ee311-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="ee311-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ee311-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="ee311-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
