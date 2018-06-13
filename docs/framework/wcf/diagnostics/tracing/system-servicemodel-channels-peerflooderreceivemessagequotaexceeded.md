---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 5c1e6c51ffd5aeafe65a67c8989f554ebf0824d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478914"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="79f47-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="79f47-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="79f47-103">Rychlost přijímání příchozích zpráv je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="79f47-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="79f47-104">Popis</span><span class="sxs-lookup"><span data-stu-id="79f47-104">Description</span></span>  
 <span data-ttu-id="79f47-105">Trasování nastane při pokusu o zpracování příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="79f47-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="79f47-106">Zprávu nelze předat konkrétní sousedním, protože byla překročena kvóta pro tento sousedním nastavit.</span><span class="sxs-lookup"><span data-stu-id="79f47-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="79f47-107">K tomu dochází, když dojde k vymazání nevyřízené položky zpráv čekající na vyřízení pro tento sousedním selhání reagovat sousedním.</span><span class="sxs-lookup"><span data-stu-id="79f47-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="79f47-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="79f47-108">Troubleshooting</span></span>  
 <span data-ttu-id="79f47-109">Omezit rychlost odesílání zpráv v mřížce.</span><span class="sxs-lookup"><span data-stu-id="79f47-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f47-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="79f47-110">See Also</span></span>  
 [<span data-ttu-id="79f47-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="79f47-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="79f47-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="79f47-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="79f47-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="79f47-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
