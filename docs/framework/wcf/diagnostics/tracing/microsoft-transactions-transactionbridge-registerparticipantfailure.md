---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475111"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="b22a9-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="b22a9-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="b22a9-103">Služba protokolu WS-AT se nepodařilo zaregistrovat účastníka pro protokol ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b22a9-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b22a9-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b22a9-104">Description</span></span>  
 <span data-ttu-id="b22a9-105">Trasovat, pokud služba MSDTC zjistí Neplatná žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="b22a9-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="b22a9-106">Příčinou může být více dokončení žádosti o registraci a interní chyby.</span><span class="sxs-lookup"><span data-stu-id="b22a9-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b22a9-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="b22a9-107">Troubleshooting</span></span>  
 <span data-ttu-id="b22a9-108">Nepokoušejte se registrace pro dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="b22a9-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="b22a9-109">Také zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="b22a9-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22a9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b22a9-110">See Also</span></span>  
 [<span data-ttu-id="b22a9-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="b22a9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b22a9-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="b22a9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b22a9-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="b22a9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
