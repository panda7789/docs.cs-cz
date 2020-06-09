---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596204"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="f5a4c-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="f5a4c-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="f5a4c-103">Zpráva o opakovaném přehrání byla znovu poslána koordinátorovi, který nereaguje.</span><span class="sxs-lookup"><span data-stu-id="f5a4c-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5a4c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="f5a4c-104">Description</span></span>  
 <span data-ttu-id="f5a4c-105">Sledováno, pokud správce místní transakce potřebuje znovu odeslat zprávu o přehrání nadřízenému koordinátora, protože v daném čase nedostala odpověď.</span><span class="sxs-lookup"><span data-stu-id="f5a4c-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f5a4c-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="f5a4c-106">Troubleshooting</span></span>  
 <span data-ttu-id="f5a4c-107">Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.</span><span class="sxs-lookup"><span data-stu-id="f5a4c-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="f5a4c-108">Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy.</span><span class="sxs-lookup"><span data-stu-id="f5a4c-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="f5a4c-109">Oba problémy budou významně snižovat propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="f5a4c-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a4c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5a4c-110">See also</span></span>

- [<span data-ttu-id="f5a4c-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="f5a4c-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="f5a4c-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="f5a4c-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f5a4c-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="f5a4c-113">Administration and Diagnostics</span></span>](../index.md)
