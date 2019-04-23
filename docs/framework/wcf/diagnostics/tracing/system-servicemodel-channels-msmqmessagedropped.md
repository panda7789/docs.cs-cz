---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 3fa5ec62c5e8ac83f3f81fb406499b7e596b3dac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161330"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="5edcb-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="5edcb-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="5edcb-103">MSMQ vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="5edcb-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5edcb-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5edcb-104">Description</span></span>  
 <span data-ttu-id="5edcb-105">Trasování označuje, že zprávy MSMQ byla vynechána.</span><span class="sxs-lookup"><span data-stu-id="5edcb-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="5edcb-106">Zprávy služby MSMQ můžete vyřadit, když Windows Communication Foundation (WCF) (používá se NetMsmqBinding nebo vazbu MsmqIntegrationBinding) se nepodařilo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="5edcb-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="5edcb-107">Tyto zprávy jsou označovány jako počet nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="5edcb-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="5edcb-108">Nezpracovatelná zpráva se zahodí, kdy `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Drop`.</span><span class="sxs-lookup"><span data-stu-id="5edcb-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="5edcb-109">Vyřazené zprávy je odebrána z fronty a není už zotavit.</span><span class="sxs-lookup"><span data-stu-id="5edcb-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="5edcb-110">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="5edcb-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5edcb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5edcb-111">See also</span></span>

- [<span data-ttu-id="5edcb-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="5edcb-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="5edcb-113">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="5edcb-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5edcb-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="5edcb-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="5edcb-115">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="5edcb-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
