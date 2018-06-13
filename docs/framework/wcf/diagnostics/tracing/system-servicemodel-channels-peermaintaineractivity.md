---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: a7f353b00796c845f5686ca2926bbe7effe09e3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480581"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="14eb9-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="14eb9-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="14eb9-103">Modul PeerMaintainer provádí konkrétní operaci (podrobnosti obsažené v textu zprávy trasování).</span><span class="sxs-lookup"><span data-stu-id="14eb9-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="14eb9-104">Popis</span><span class="sxs-lookup"><span data-stu-id="14eb9-104">Description</span></span>  
 <span data-ttu-id="14eb9-105">Trasování nastane během různé PeerMaintainer operace.</span><span class="sxs-lookup"><span data-stu-id="14eb9-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="14eb9-106">PeerMaintainer je interní součást Uzel PeerNode.</span><span class="sxs-lookup"><span data-stu-id="14eb9-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="14eb9-107">Každou minutu nebo každých 32 zprávy přijaté, odešle zprávu LinkUtility pro své okolí s statistické údaje o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplikáty, untampered).</span><span class="sxs-lookup"><span data-stu-id="14eb9-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="14eb9-108">To vám pomůže určit konkrétní sousedním odkaz nástroj.</span><span class="sxs-lookup"><span data-stu-id="14eb9-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="14eb9-109">Přibližně každých pět minut, funkce maintainer kontroluje stav sousedním připojení.</span><span class="sxs-lookup"><span data-stu-id="14eb9-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="14eb9-110">Pokud počet připojení sousedním překračuje ideální, funkce maintainer vyřazuje vypnout minimálně užitečné připojení.</span><span class="sxs-lookup"><span data-stu-id="14eb9-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="14eb9-111">Pokud nejsou k dispozici dostatek připojení, funkce maintainer získá nové připojení.</span><span class="sxs-lookup"><span data-stu-id="14eb9-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14eb9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="14eb9-112">See Also</span></span>  
 [<span data-ttu-id="14eb9-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="14eb9-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="14eb9-114">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="14eb9-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="14eb9-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="14eb9-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
