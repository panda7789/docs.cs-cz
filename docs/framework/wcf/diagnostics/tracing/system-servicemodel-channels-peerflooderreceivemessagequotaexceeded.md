---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596087"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="1e6bf-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="1e6bf-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="1e6bf-103">Míra příchozího příjmu zpráv je příliš vysoká.</span><span class="sxs-lookup"><span data-stu-id="1e6bf-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e6bf-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1e6bf-104">Description</span></span>  
 <span data-ttu-id="1e6bf-105">K tomuto trasování dochází při pokusu o zpracování příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="1e6bf-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="1e6bf-106">Zpráva nemohla být předána do konkrétního souseda, protože byla překročena kvóta nastavená pro daný sousední uzel.</span><span class="sxs-lookup"><span data-stu-id="1e6bf-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="1e6bf-107">K tomu dochází, když nereagující sousední uzel nevymaže nevyřízené položky zpráv, které čekají na vyřízení pro daný sousední uzel.</span><span class="sxs-lookup"><span data-stu-id="1e6bf-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1e6bf-108">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="1e6bf-108">Troubleshooting</span></span>  
 <span data-ttu-id="1e6bf-109">Snižte rychlost odesílání zpráv v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="1e6bf-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e6bf-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e6bf-110">See also</span></span>

- [<span data-ttu-id="1e6bf-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="1e6bf-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="1e6bf-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="1e6bf-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1e6bf-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="1e6bf-113">Administration and Diagnostics</span></span>](../index.md)
