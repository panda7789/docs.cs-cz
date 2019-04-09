---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126032"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="2f108-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="2f108-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="2f108-103">Modul PeerMaintainer je provádění konkrétní operace (informace obsažené v textu zprávy trasování).</span><span class="sxs-lookup"><span data-stu-id="2f108-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f108-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2f108-104">Description</span></span>  
 <span data-ttu-id="2f108-105">Trasování nastane při různých operací PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="2f108-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="2f108-106">PeerMaintainer je vnitřní komponenta PeerNode.</span><span class="sxs-lookup"><span data-stu-id="2f108-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="2f108-107">Každou minutu nebo každých 32 zpráv přijme, odešle zpráva LinkUtility k jejím sousedům se statistikami o tom, kolik zprávy se vyměňují a kolik jsou užitečné (bez duplicitní, untampered).</span><span class="sxs-lookup"><span data-stu-id="2f108-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="2f108-108">To vám pomůže určit konkrétní sousední propojení nástroje.</span><span class="sxs-lookup"><span data-stu-id="2f108-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="2f108-109">Přibližně každých pět minut, funkce maintainer zkontroluje stav připojení sousedem.</span><span class="sxs-lookup"><span data-stu-id="2f108-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="2f108-110">Pokud počet sousední připojení překročí ideální částka, funkce maintainer ořezává vypnout nejméně užitečné připojení.</span><span class="sxs-lookup"><span data-stu-id="2f108-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="2f108-111">Pokud nejsou k dispozici dostatek připojení, funkce maintainer získává nové připojení.</span><span class="sxs-lookup"><span data-stu-id="2f108-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f108-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f108-112">See also</span></span>

- [<span data-ttu-id="2f108-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="2f108-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="2f108-114">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="2f108-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2f108-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="2f108-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
