---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e7e87c379c84829934a929ec27bd5dacde3931f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="52e4f-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="52e4f-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="52e4f-103">Opakování opětovného přehrání zpráva byla odeslána reagovat coordinator.</span><span class="sxs-lookup"><span data-stu-id="52e4f-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="52e4f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="52e4f-104">Description</span></span>  
 <span data-ttu-id="52e4f-105">Trasovat potřeby formou opakovaného přehrávání zprávy, která se nadřízený koordinátor znovu odeslat, protože nepřijala odpověď dané množství času místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="52e4f-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="52e4f-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="52e4f-106">Troubleshooting</span></span>  
 <span data-ttu-id="52e4f-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="52e4f-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="52e4f-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="52e4f-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="52e4f-109">Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="52e4f-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e4f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="52e4f-110">See Also</span></span>  
 [<span data-ttu-id="52e4f-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="52e4f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="52e4f-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="52e4f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="52e4f-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="52e4f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
