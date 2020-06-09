---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601410"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="9e668-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="9e668-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="9e668-103">Nepodařilo se dokončit vyjednávání protokolu OleTransactions pro zadaný koordinační kontext.</span><span class="sxs-lookup"><span data-stu-id="9e668-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e668-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9e668-104">Description</span></span>  
 <span data-ttu-id="9e668-105">Sledováno, když příchozí transakce s OleTx informacemi nedokáže použít připojené OleTx informace, a místo toho se vrátí k použití WS-AT.</span><span class="sxs-lookup"><span data-stu-id="9e668-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9e668-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="9e668-106">Troubleshooting</span></span>  
 <span data-ttu-id="9e668-107">Označuje potenciální problém s komunikací služby MSDTC RPC mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="9e668-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="9e668-108">Pokud se mnoho z těchto trasování objeví v protokolu, může to vést k drastickému poklesu výkonu.</span><span class="sxs-lookup"><span data-stu-id="9e668-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="9e668-109">Pokud OleTx není žádoucí, nastavte `OleTxUpgradeEnabled` na hodnotu 0 v konfiguraci registru WS-AT.</span><span class="sxs-lookup"><span data-stu-id="9e668-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e668-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e668-110">See also</span></span>

- [<span data-ttu-id="9e668-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="9e668-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9e668-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="9e668-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9e668-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="9e668-113">Administration and Diagnostics</span></span>](../index.md)
