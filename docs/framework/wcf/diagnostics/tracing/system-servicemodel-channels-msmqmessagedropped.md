---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: ad05a2b8552cc09d45e950e2c3336d86be918963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479128"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="13a5f-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="13a5f-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="13a5f-103">MSMQ vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="13a5f-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="13a5f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="13a5f-104">Description</span></span>  
 <span data-ttu-id="13a5f-105">Trasování označuje, že služby MSMQ zpráva byla vyřazena.</span><span class="sxs-lookup"><span data-stu-id="13a5f-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="13a5f-106">Zprávy služby MSMQ můžete vyřadit, když Windows Communication Foundation (WCF) (používá se s – NetMsmqBinding nebo – MsmqIntegrationBinding) se nepodařilo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="13a5f-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="13a5f-107">Takové zprávy se označují jako poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="13a5f-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="13a5f-108">Nezpracovatelná zpráva je vynechána, kdy `ReceiveErrorHandling` – NetMsmqBinding nebo – MsmqIntegrationBinding je nastavena na `Drop`.</span><span class="sxs-lookup"><span data-stu-id="13a5f-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="13a5f-109">Vyřazené zprávy je odebrána z fronty a nadále již není použitelná pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="13a5f-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="13a5f-110">V tématu [zpracování zpráv Poison](http://go.microsoft.com/fwlink/?LinkID=99546) další podrobnosti o kdy začnou poškozených zpráv a postup konfigurace služby pro správně zpracovat.</span><span class="sxs-lookup"><span data-stu-id="13a5f-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a5f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="13a5f-111">See Also</span></span>  
 [<span data-ttu-id="13a5f-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="13a5f-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="13a5f-113">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="13a5f-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="13a5f-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="13a5f-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="13a5f-115">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="13a5f-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
