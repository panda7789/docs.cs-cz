---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596074"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="bc1f8-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="bc1f8-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="bc1f8-103">Modul činnost PeerMaintainer provádí konkrétní operaci (podrobnosti najdete v těle trasovací zprávy).</span><span class="sxs-lookup"><span data-stu-id="bc1f8-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="bc1f8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="bc1f8-104">Description</span></span>  
 <span data-ttu-id="bc1f8-105">K tomuto trasování dochází během různých činnost PeerMaintainer operací.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="bc1f8-106">Činnost PeerMaintainer je interní komponenta PeerNode.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="bc1f8-107">Každou minutu nebo všechny přijaté zprávy 32 pošle zprávu LinkUtility svým sousedům se statistikou o počtu vyměňovaných zpráv a počtu užitečných (neoprávněných duplicit).</span><span class="sxs-lookup"><span data-stu-id="bc1f8-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="bc1f8-108">To pomáhá určit určitý sousední Nástroj pro propojení.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="bc1f8-109">Přibližně každých pět minut udržuje údržba stav sousedních připojení.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="bc1f8-110">Pokud počet sousedních připojení překročí ideální množství, vyřadí ho údržba nejméně užitečná připojení.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="bc1f8-111">Pokud není k dispozici dostatek připojení, údržba získá nová připojení.</span><span class="sxs-lookup"><span data-stu-id="bc1f8-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1f8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc1f8-112">See also</span></span>

- [<span data-ttu-id="bc1f8-113">Trasování</span><span class="sxs-lookup"><span data-stu-id="bc1f8-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="bc1f8-114">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="bc1f8-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bc1f8-115">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="bc1f8-115">Administration and Diagnostics</span></span>](../index.md)
