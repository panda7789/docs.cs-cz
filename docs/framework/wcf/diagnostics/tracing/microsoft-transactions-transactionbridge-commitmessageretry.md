---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f37bc252e12aef94d77c0745d36b5c8232a169eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599734"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="70e0c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="70e0c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="70e0c-103">Zpráva potvrzení byla znovu poslána účastníkovi, který nereagoval.</span><span class="sxs-lookup"><span data-stu-id="70e0c-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="70e0c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="70e0c-104">Description</span></span>  
 <span data-ttu-id="70e0c-105">Sledováno, pokud správce místní transakce potřebuje znovu odeslat zprávu potvrzení podřízenému účastníkovi, protože v daném čase nedostal odpověď.</span><span class="sxs-lookup"><span data-stu-id="70e0c-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="70e0c-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="70e0c-106">Troubleshooting</span></span>  
 <span data-ttu-id="70e0c-107">Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.</span><span class="sxs-lookup"><span data-stu-id="70e0c-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="70e0c-108">Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy.</span><span class="sxs-lookup"><span data-stu-id="70e0c-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="70e0c-109">Oba problémy budou významně snižovat propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="70e0c-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e0c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="70e0c-110">See also</span></span>

- [<span data-ttu-id="70e0c-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="70e0c-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="70e0c-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="70e0c-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="70e0c-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="70e0c-113">Administration and Diagnostics</span></span>](../index.md)
