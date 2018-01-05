---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b036673e6823bcb15358099ac4e4a49b845f2c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="08492-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="08492-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="08492-103">Opakování připravené zpráva byla odeslána reagovat coordinator.</span><span class="sxs-lookup"><span data-stu-id="08492-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="08492-104">Popis</span><span class="sxs-lookup"><span data-stu-id="08492-104">Description</span></span>  
 <span data-ttu-id="08492-105">Trasovat potřeby znovu odeslat zprávu připravené k nadřazené coordinator, protože nepřijala odpověď dané množství času místní správce transakcí nebo</span><span class="sxs-lookup"><span data-stu-id="08492-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="08492-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="08492-106">Troubleshooting</span></span>  
 <span data-ttu-id="08492-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="08492-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="08492-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="08492-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="08492-109">Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="08492-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08492-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="08492-110">See Also</span></span>  
 [<span data-ttu-id="08492-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="08492-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="08492-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="08492-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="08492-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="08492-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
