---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 3c398aa13a8cd2b87068216d3c07fb29e1a27c3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168100"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="17f34-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="17f34-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="17f34-103">Opakování zpráva potvrzení byla odeslána poslána účastníkovi.</span><span class="sxs-lookup"><span data-stu-id="17f34-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="17f34-104">Popis</span><span class="sxs-lookup"><span data-stu-id="17f34-104">Description</span></span>  
 <span data-ttu-id="17f34-105">Trasovaná potřeby znovu odeslat zprávu potvrzení do podřízeného člena, protože neobdržela odpověď v daném čase místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="17f34-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="17f34-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="17f34-106">Troubleshooting</span></span>  
 <span data-ttu-id="17f34-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="17f34-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="17f34-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="17f34-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="17f34-109">Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="17f34-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f34-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17f34-110">See also</span></span>

- [<span data-ttu-id="17f34-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="17f34-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="17f34-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="17f34-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="17f34-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="17f34-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
