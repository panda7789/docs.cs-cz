---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997747"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="fa50f-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="fa50f-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="fa50f-103">Službě protokolu WS-AT se nepodařilo zaregistrovat účastníka pro kontrolní protokol.</span><span class="sxs-lookup"><span data-stu-id="fa50f-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa50f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fa50f-104">Description</span></span>  
 <span data-ttu-id="fa50f-105">Trasovaná Pokud MSDTC zjistí Neplatná žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="fa50f-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="fa50f-106">Může to být způsobeno několika dokončení žádosti o registraci a vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="fa50f-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fa50f-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="fa50f-107">Troubleshooting</span></span>  
 <span data-ttu-id="fa50f-108">Nepokoušejte se zaregistrovat se na dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="fa50f-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="fa50f-109">Také kontrolovat stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="fa50f-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa50f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa50f-110">See also</span></span>

- [<span data-ttu-id="fa50f-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="fa50f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fa50f-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fa50f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fa50f-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="fa50f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
