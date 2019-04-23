---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097561"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="58960-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="58960-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="58960-103">Vyjednávání protokolu OleTransactions se nepodařilo dokončit pro zadaný koordinační kontext.</span><span class="sxs-lookup"><span data-stu-id="58960-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="58960-104">Popis</span><span class="sxs-lookup"><span data-stu-id="58960-104">Description</span></span>  
 <span data-ttu-id="58960-105">Sledovat příchozí transakce s informacemi o OleTx nemůže použít připojené OleTx informace, a bude fall zpět a místo toho použít WS-AT.</span><span class="sxs-lookup"><span data-stu-id="58960-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="58960-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="58960-106">Troubleshooting</span></span>  
 <span data-ttu-id="58960-107">Označuje potenciální problém s MSDTC RPC komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="58960-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="58960-108">Pokud mnoho z těchto trasování v protokolu zobrazily, může dojít k závažný snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="58960-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="58960-109">Pokud OleTx není žádoucí, nastavte `OleTxUpgradeEnabled` na 0 v konfiguraci WS-AT registru.</span><span class="sxs-lookup"><span data-stu-id="58960-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58960-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58960-110">See also</span></span>

- [<span data-ttu-id="58960-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="58960-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="58960-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="58960-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="58960-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="58960-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
