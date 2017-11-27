---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="04529-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="04529-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="04529-103">Modul PeerMaintainer provádí konkrétní operaci (podrobnosti obsažené v textu zprávy trasování).</span><span class="sxs-lookup"><span data-stu-id="04529-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="04529-104">Popis</span><span class="sxs-lookup"><span data-stu-id="04529-104">Description</span></span>  
 <span data-ttu-id="04529-105">Trasování nastane během různé PeerMaintainer operace.</span><span class="sxs-lookup"><span data-stu-id="04529-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="04529-106">PeerMaintainer je interní součást Uzel PeerNode.</span><span class="sxs-lookup"><span data-stu-id="04529-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="04529-107">Každou minutu nebo každých 32 zprávy přijaté, odešle zprávu LinkUtility pro své okolí s statistické údaje o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplikáty, untampered).</span><span class="sxs-lookup"><span data-stu-id="04529-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="04529-108">To vám pomůže určit konkrétní sousedním odkaz nástroj.</span><span class="sxs-lookup"><span data-stu-id="04529-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="04529-109">Přibližně každých pět minut, funkce maintainer kontroluje stav sousedním připojení.</span><span class="sxs-lookup"><span data-stu-id="04529-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="04529-110">Pokud počet připojení sousedním překračuje ideální, funkce maintainer vyřazuje vypnout minimálně užitečné připojení.</span><span class="sxs-lookup"><span data-stu-id="04529-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="04529-111">Pokud nejsou k dispozici dostatek připojení, funkce maintainer získá nové připojení.</span><span class="sxs-lookup"><span data-stu-id="04529-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04529-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="04529-112">See Also</span></span>  
 [<span data-ttu-id="04529-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="04529-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="04529-114">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="04529-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="04529-115">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="04529-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
