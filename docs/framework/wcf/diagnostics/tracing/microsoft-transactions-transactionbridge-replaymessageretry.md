---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 0c9e79709f5929e1fa123a8d1695ca720046e9e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190870"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="ec2eb-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="ec2eb-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="ec2eb-103">Přehrání opakování zpráva se odeslala na poslána koordinátorovi, který.</span><span class="sxs-lookup"><span data-stu-id="ec2eb-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ec2eb-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ec2eb-104">Description</span></span>  
 <span data-ttu-id="ec2eb-105">Trasovaná v případě potřeby místní správce transakcí se opětovné poslání odpověď na dokonalá koordinátor, protože neobdržela odpověď v daném čase.</span><span class="sxs-lookup"><span data-stu-id="ec2eb-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ec2eb-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="ec2eb-106">Troubleshooting</span></span>  
 <span data-ttu-id="ec2eb-107">Prošetření potenciálních sítě nebo problémů s produktem, které brání znemožňuje doručování včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="ec2eb-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="ec2eb-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="ec2eb-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="ec2eb-109">Oba problémy výrazně zkrátí propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="ec2eb-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2eb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec2eb-110">See also</span></span>

- [<span data-ttu-id="ec2eb-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="ec2eb-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ec2eb-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="ec2eb-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ec2eb-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="ec2eb-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
