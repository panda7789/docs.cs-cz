---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="c0c87-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="c0c87-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="c0c87-103">Vyjednávání protokolu OleTransactions se nepodařilo dokončit pro koordinaci zadaný kontext.</span><span class="sxs-lookup"><span data-stu-id="c0c87-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c0c87-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c87-104">Description</span></span>  
 <span data-ttu-id="c0c87-105">Sledovat, když příchozí transakci s informacemi o OleTx nemůže použít připojené OleTx informace a bude patří zpět a místo toho použít WS-AT.</span><span class="sxs-lookup"><span data-stu-id="c0c87-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c0c87-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="c0c87-106">Troubleshooting</span></span>  
 <span data-ttu-id="c0c87-107">Označuje potenciální problém s komunikací služby MSDTC RPC mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="c0c87-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="c0c87-108">Pokud mnoho z těchto trasování se zobrazí v protokolu, může způsobit závažný snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="c0c87-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="c0c87-109">V případě potřeby OleTx není nastavena `OleTxUpgradeEnabled` na 0 v konfiguraci registrů WS-AT.</span><span class="sxs-lookup"><span data-stu-id="c0c87-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c87-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0c87-110">See Also</span></span>  
 [<span data-ttu-id="c0c87-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="c0c87-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c0c87-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c0c87-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c0c87-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="c0c87-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
