---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: d939d525fd1c7e8f41cccbc3ca7af9726f22bdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571428"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="fe799-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="fe799-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="fe799-103">Opakování zpráva potvrzení byla odeslána poslána účastníkovi.</span><span class="sxs-lookup"><span data-stu-id="fe799-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fe799-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fe799-104">Description</span></span>  
 <span data-ttu-id="fe799-105">Trasovaná potřeby znovu odeslat zprávu potvrzení do podřízeného člena, protože neobdržela odpověď v daném čase místní správce transakcí.</span><span class="sxs-lookup"><span data-stu-id="fe799-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fe799-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="fe799-106">Troubleshooting</span></span>  
 <span data-ttu-id="fe799-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="fe799-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="fe799-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="fe799-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="fe799-109">Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="fe799-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe799-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe799-110">See also</span></span>
- [<span data-ttu-id="fe799-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="fe799-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fe799-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fe799-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fe799-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="fe799-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
