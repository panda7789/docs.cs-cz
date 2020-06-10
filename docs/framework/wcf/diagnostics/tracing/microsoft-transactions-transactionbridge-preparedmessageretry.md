---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 50dd3070525bbc6d36956b25dee587ec7864d3ff
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594306"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="e9fef-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="e9fef-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="e9fef-103">Připravená zpráva byla znovu poslána koordinátorovi, který nereaguje.</span><span class="sxs-lookup"><span data-stu-id="e9fef-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e9fef-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e9fef-104">Description</span></span>  
 <span data-ttu-id="e9fef-105">Sledováno, pokud správce místní transakce potřebuje znovu odeslat připravenou zprávu nadřazenému koordinátorovi, protože nedostal odpověď v daném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="e9fef-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e9fef-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="e9fef-106">Troubleshooting</span></span>  
 <span data-ttu-id="e9fef-107">Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.</span><span class="sxs-lookup"><span data-stu-id="e9fef-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="e9fef-108">Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy.</span><span class="sxs-lookup"><span data-stu-id="e9fef-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="e9fef-109">Oba problémy budou významně snižovat propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="e9fef-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fef-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9fef-110">See also</span></span>

- [<span data-ttu-id="e9fef-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="e9fef-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="e9fef-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e9fef-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e9fef-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e9fef-113">Administration and Diagnostics</span></span>](../index.md)
