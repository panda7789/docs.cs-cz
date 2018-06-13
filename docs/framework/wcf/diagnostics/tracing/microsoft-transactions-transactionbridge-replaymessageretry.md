---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: d000447245d973916dfe0df9af5c46b6fa822e32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475127"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="88bf1-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="88bf1-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="88bf1-103">Opakování opětovného přehrání zpráva byla odeslána reagovat coordinator.</span><span class="sxs-lookup"><span data-stu-id="88bf1-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88bf1-104">Popis</span><span class="sxs-lookup"><span data-stu-id="88bf1-104">Description</span></span>  
 <span data-ttu-id="88bf1-105">Trasovat potřeby formou opakovaného přehrávání zprávy, která se nadřízený koordinátor znovu odeslat, protože nepřijala odpověď dané množství času místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="88bf1-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="88bf1-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="88bf1-106">Troubleshooting</span></span>  
 <span data-ttu-id="88bf1-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="88bf1-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="88bf1-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="88bf1-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="88bf1-109">Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="88bf1-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bf1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="88bf1-110">See Also</span></span>  
 [<span data-ttu-id="88bf1-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="88bf1-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="88bf1-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="88bf1-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="88bf1-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="88bf1-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
