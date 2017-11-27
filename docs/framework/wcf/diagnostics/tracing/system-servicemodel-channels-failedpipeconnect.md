---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a64f5885fd32d2486c90ebe4f8e0c739a025d0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="fefa1-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="fefa1-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="fefa1-103">Pokus o připojení ke koncovému bodu pojmenovaný kanál se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="fefa1-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="fefa1-104">Další pokus se uskuteční během zadaného časového limitu.</span><span class="sxs-lookup"><span data-stu-id="fefa1-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fefa1-105">Popis</span><span class="sxs-lookup"><span data-stu-id="fefa1-105">Description</span></span>  
 <span data-ttu-id="fefa1-106">Informační trasování označuje selhání připojení ke koncovému bodu pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="fefa1-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="fefa1-107">Toto může nastat, pokud koncový bod pojmenovaný kanál nebyl nalezen nebo je zaneprázdněný.</span><span class="sxs-lookup"><span data-stu-id="fefa1-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="fefa1-108">Další pokusy, jsou odděleny krátkou dobu, dokud jeden neuspěje nebo OpenTimeout vyprší.</span><span class="sxs-lookup"><span data-stu-id="fefa1-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefa1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="fefa1-109">See Also</span></span>  
 [<span data-ttu-id="fefa1-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="fefa1-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fefa1-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fefa1-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fefa1-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="fefa1-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
