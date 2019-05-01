---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: d8acdb2f94e752860025ee2963aa78682b43b079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997890"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="67d2a-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="67d2a-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="67d2a-103">Opakování připravená zpráva byla odeslána poslána koordinátorovi, který.</span><span class="sxs-lookup"><span data-stu-id="67d2a-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="67d2a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="67d2a-104">Description</span></span>  
 <span data-ttu-id="67d2a-105">Trasovaná v případě potřeby místní správce transakcí znovu odeslat zprávu připravený na dokonalá koordinátor, protože neobdržela odpověď v daném čase /</span><span class="sxs-lookup"><span data-stu-id="67d2a-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="67d2a-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="67d2a-106">Troubleshooting</span></span>  
 <span data-ttu-id="67d2a-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="67d2a-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="67d2a-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="67d2a-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="67d2a-109">Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="67d2a-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d2a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67d2a-110">See also</span></span>

- [<span data-ttu-id="67d2a-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="67d2a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="67d2a-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="67d2a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="67d2a-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="67d2a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
