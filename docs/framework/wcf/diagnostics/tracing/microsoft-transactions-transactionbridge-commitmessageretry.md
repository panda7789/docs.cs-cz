---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f1092dd335be793fb3d2212b7b9398cc69d2f79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474282"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="2652b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="2652b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="2652b-103">Opakování potvrzení zpráva byla odeslána reagovat účastník.</span><span class="sxs-lookup"><span data-stu-id="2652b-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2652b-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2652b-104">Description</span></span>  
 <span data-ttu-id="2652b-105">Sledovat v případě potřeby místní správce transakcí o doručení zprávy potvrzení k podřízené účastník, protože nepřijala odpověď dané množství času.</span><span class="sxs-lookup"><span data-stu-id="2652b-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2652b-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="2652b-106">Troubleshooting</span></span>  
 <span data-ttu-id="2652b-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="2652b-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="2652b-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="2652b-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="2652b-109">Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="2652b-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2652b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2652b-110">See Also</span></span>  
 [<span data-ttu-id="2652b-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="2652b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2652b-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="2652b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2652b-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="2652b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
