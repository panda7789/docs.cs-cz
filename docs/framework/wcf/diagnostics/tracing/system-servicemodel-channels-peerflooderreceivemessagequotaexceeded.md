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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="9367d-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="9367d-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="9367d-103">Rychlost přijímání příchozích zpráv je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="9367d-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9367d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9367d-104">Description</span></span>  
 <span data-ttu-id="9367d-105">Trasování nastane při pokusu o zpracování příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="9367d-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="9367d-106">Zprávu nelze předat konkrétní sousedním, protože byla překročena kvóta pro tento sousedním nastavit.</span><span class="sxs-lookup"><span data-stu-id="9367d-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="9367d-107">K tomu dochází, když dojde k vymazání nevyřízené položky zpráv čekající na vyřízení pro tento sousedním selhání reagovat sousedním.</span><span class="sxs-lookup"><span data-stu-id="9367d-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9367d-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="9367d-108">Troubleshooting</span></span>  
 <span data-ttu-id="9367d-109">Omezit rychlost odesílání zpráv v mřížce.</span><span class="sxs-lookup"><span data-stu-id="9367d-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9367d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="9367d-110">See Also</span></span>  
 [<span data-ttu-id="9367d-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="9367d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9367d-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="9367d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9367d-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="9367d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
