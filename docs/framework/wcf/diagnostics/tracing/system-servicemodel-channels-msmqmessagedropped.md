---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="a27e1-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="a27e1-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="a27e1-103">MSMQ vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="a27e1-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a27e1-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a27e1-104">Description</span></span>  
 <span data-ttu-id="a27e1-105">Trasování označuje, že služby MSMQ zpráva byla vyřazena.</span><span class="sxs-lookup"><span data-stu-id="a27e1-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="a27e1-106">Může být přetažen MSMQ zprávy, když [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a27e1-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="a27e1-107">Takové zprávy se označují jako poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="a27e1-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="a27e1-108">Nezpracovatelná zpráva je vynechána, kdy `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Drop`.</span><span class="sxs-lookup"><span data-stu-id="a27e1-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="a27e1-109">Vyřazené zprávy je odebrána z fronty a nadále již není použitelná pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="a27e1-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="a27e1-110">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a27e1-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27e1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a27e1-111">See Also</span></span>  
 [<span data-ttu-id="a27e1-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="a27e1-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a27e1-113">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a27e1-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a27e1-114">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="a27e1-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="a27e1-115">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="a27e1-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
