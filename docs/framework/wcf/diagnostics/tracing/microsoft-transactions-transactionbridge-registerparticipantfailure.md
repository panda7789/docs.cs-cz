---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: b94c017f6ed3a76a6bc5ed2cb970877ad18ef9ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610419"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="34e4a-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="34e4a-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="34e4a-103">Službě protokolu WS-AT se nepodařilo zaregistrovat účastníka pro kontrolní protokol.</span><span class="sxs-lookup"><span data-stu-id="34e4a-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34e4a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="34e4a-104">Description</span></span>  
 <span data-ttu-id="34e4a-105">Trasovaná Pokud MSDTC zjistí Neplatná žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="34e4a-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="34e4a-106">Může to být způsobeno několika dokončení žádosti o registraci a vnitřní chyby.</span><span class="sxs-lookup"><span data-stu-id="34e4a-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="34e4a-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="34e4a-107">Troubleshooting</span></span>  
 <span data-ttu-id="34e4a-108">Nepokoušejte se zaregistrovat se na dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="34e4a-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="34e4a-109">Také kontrolovat stav řetězce v rámci zpráva trasování, má-li zjistit, jestli existuje jakoukoli užitečné.</span><span class="sxs-lookup"><span data-stu-id="34e4a-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e4a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34e4a-110">See also</span></span>
- [<span data-ttu-id="34e4a-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="34e4a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="34e4a-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="34e4a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="34e4a-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="34e4a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
