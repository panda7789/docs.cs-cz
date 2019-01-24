---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6218948e89288e76034d7c3f032f3c585e286c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570535"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="8ba7c-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="8ba7c-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="8ba7c-103">MSMQ vyřadit zprávu.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ba7c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8ba7c-104">Description</span></span>  
 <span data-ttu-id="8ba7c-105">Trasování označuje, že zprávy MSMQ byla vynechána.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="8ba7c-106">Zprávy služby MSMQ můžete vyřadit, když Windows Communication Foundation (WCF) (používá se NetMsmqBinding nebo vazbu MsmqIntegrationBinding) se nepodařilo zpracovat.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="8ba7c-107">Tyto zprávy jsou označovány jako počet nezpracovatelných zpráv.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="8ba7c-108">Nezpracovatelná zpráva se zahodí, kdy `ReceiveErrorHandling` NetMsmqBinding nebo vazbu MsmqIntegrationBinding je nastavena na `Drop`.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="8ba7c-109">Vyřazené zprávy je odebrána z fronty a není už zotavit.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="8ba7c-110">Zobrazit [zpracování zpráv Poison](https://go.microsoft.com/fwlink/?LinkID=99546) podrobné informace o při stát nezpracovatelných zpráv a způsob konfigurace vaší služby k odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="8ba7c-110">See [Poison-Message Handling](https://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba7c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ba7c-111">See also</span></span>
- [<span data-ttu-id="8ba7c-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="8ba7c-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8ba7c-113">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8ba7c-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8ba7c-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8ba7c-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="8ba7c-115">Zpracování zpráv Poison</span><span class="sxs-lookup"><span data-stu-id="8ba7c-115">Poison-Message Handling</span></span>](https://go.microsoft.com/fwlink/?LinkID=99546)
