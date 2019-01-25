---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: f168cb24d87f3159a1ea41003c2ffa7041ce8c09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710440"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="8c63d-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8c63d-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="8c63d-103">Přípravy opakování zpráva byla odeslána poslána účastníkovi.</span><span class="sxs-lookup"><span data-stu-id="8c63d-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8c63d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8c63d-104">Description</span></span>  
 <span data-ttu-id="8c63d-105">Trasovaná potřeby znovu odeslat zprávu připravit podřízené účastníkovi, protože neobdržela odpověď v daném čase místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="8c63d-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8c63d-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="8c63d-106">Troubleshooting</span></span>  
 <span data-ttu-id="8c63d-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="8c63d-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8c63d-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="8c63d-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8c63d-109">Oba problémy může výrazně omezit propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="8c63d-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c63d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c63d-110">See also</span></span>
- [<span data-ttu-id="8c63d-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="8c63d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8c63d-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8c63d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8c63d-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8c63d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
