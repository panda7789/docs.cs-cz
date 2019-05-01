---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950641"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="adf32-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="adf32-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="adf32-103">Rychlost přijímání příchozích zpráv je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="adf32-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="adf32-104">Popis</span><span class="sxs-lookup"><span data-stu-id="adf32-104">Description</span></span>  
 <span data-ttu-id="adf32-105">Trasování nastane při pokusu o zpracování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="adf32-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="adf32-106">Zprávu nelze předat konkrétní sousední, protože se překročila kvótu nastavenou pro tuto sousední.</span><span class="sxs-lookup"><span data-stu-id="adf32-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="adf32-107">Příčinou je selhání reagovat sousední vymazání nevyřízených položek nevyřízené zprávy pro tuto sousedem.</span><span class="sxs-lookup"><span data-stu-id="adf32-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="adf32-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="adf32-108">Troubleshooting</span></span>  
 <span data-ttu-id="adf32-109">Snížit rychlost odesílání zpráv v rámci síť.</span><span class="sxs-lookup"><span data-stu-id="adf32-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf32-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adf32-110">See also</span></span>

- [<span data-ttu-id="adf32-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="adf32-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="adf32-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="adf32-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="adf32-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="adf32-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
