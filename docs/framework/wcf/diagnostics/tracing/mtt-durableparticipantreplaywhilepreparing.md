---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fe88e70ab4955305d78baa1158cd73a93ba2ed2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476317"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="37d3a-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="37d3a-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="37d3a-103">Služba Protokol WS-AT přijala zprávu opětovného přehrání z trvalého účastníka, které neodpovídají na přípravu.</span><span class="sxs-lookup"><span data-stu-id="37d3a-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="37d3a-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="37d3a-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="37d3a-105">Popis</span><span class="sxs-lookup"><span data-stu-id="37d3a-105">Description</span></span>  
 <span data-ttu-id="37d3a-106">Trasovat, pokud bylo přijato formou opakovaného přehrávání zprávy trvalého účastníka stále připravuje.</span><span class="sxs-lookup"><span data-stu-id="37d3a-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="37d3a-107">Tato zpráva neplatné pro tento stav je a transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="37d3a-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="37d3a-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="37d3a-108">Troubleshooting</span></span>  
 <span data-ttu-id="37d3a-109">Tato chyba může indiate, že trvalého účastníka (včetně podřízených TransactionManagers) došlo k zotavení z chyby, ale je jistí výstup transakce a požádat o jeho stav.</span><span class="sxs-lookup"><span data-stu-id="37d3a-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d3a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="37d3a-110">See Also</span></span>  
 [<span data-ttu-id="37d3a-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="37d3a-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="37d3a-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="37d3a-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="37d3a-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="37d3a-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
