---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3919e48925eeb0d197c23da582836dec5bf6438
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="971ec-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="971ec-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="971ec-103">Rychlost přijímání příchozích zpráv je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="971ec-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="971ec-104">Popis</span><span class="sxs-lookup"><span data-stu-id="971ec-104">Description</span></span>  
 <span data-ttu-id="971ec-105">Trasování nastane při pokusu o zpracování příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="971ec-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="971ec-106">Zprávu nelze předat konkrétní sousedním, protože byla překročena kvóta pro tento sousedním nastavit.</span><span class="sxs-lookup"><span data-stu-id="971ec-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="971ec-107">K tomu dochází, když dojde k vymazání nevyřízené položky zpráv čekající na vyřízení pro tento sousedním selhání reagovat sousedním.</span><span class="sxs-lookup"><span data-stu-id="971ec-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="971ec-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="971ec-108">Troubleshooting</span></span>  
 <span data-ttu-id="971ec-109">Omezit rychlost odesílání zpráv v mřížce.</span><span class="sxs-lookup"><span data-stu-id="971ec-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971ec-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="971ec-110">See Also</span></span>  
 [<span data-ttu-id="971ec-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="971ec-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="971ec-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="971ec-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="971ec-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="971ec-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
