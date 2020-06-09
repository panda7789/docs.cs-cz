---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599673"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="7ad38-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="7ad38-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="7ad38-103">Službě protokolu WS-AT se nepodařilo zaregistrovat účastníka pro kontrolní protokol.</span><span class="sxs-lookup"><span data-stu-id="7ad38-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7ad38-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7ad38-104">Description</span></span>  
 <span data-ttu-id="7ad38-105">Sledováno, pokud služba MSDTC detekuje neplatnou žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="7ad38-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="7ad38-106">To může být způsobeno několika žádostmi o registraci dokončení a interními chybami.</span><span class="sxs-lookup"><span data-stu-id="7ad38-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7ad38-107">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="7ad38-107">Troubleshooting</span></span>  
 <span data-ttu-id="7ad38-108">Nepokoušejte se registrovat na dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="7ad38-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="7ad38-109">Také zkontrolujte řetězec stavu v rámci zprávy trasování a určete, zda existuje nějaká položka, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7ad38-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad38-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad38-110">See also</span></span>

- [<span data-ttu-id="7ad38-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="7ad38-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="7ad38-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="7ad38-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7ad38-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="7ad38-113">Administration and Diagnostics</span></span>](../index.md)
