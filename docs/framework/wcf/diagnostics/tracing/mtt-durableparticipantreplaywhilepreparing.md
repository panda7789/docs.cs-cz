---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 375bb5902640ba0816217aec161834d79e9765ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="2af24-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="2af24-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="2af24-103">Služba Protokol WS-AT přijala zprávu opětovného přehrání z trvalého účastníka, které neodpovídají na přípravu.</span><span class="sxs-lookup"><span data-stu-id="2af24-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="2af24-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="2af24-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2af24-105">Popis</span><span class="sxs-lookup"><span data-stu-id="2af24-105">Description</span></span>  
 <span data-ttu-id="2af24-106">Trasovat, pokud bylo přijato formou opakovaného přehrávání zprávy trvalého účastníka stále připravuje.</span><span class="sxs-lookup"><span data-stu-id="2af24-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="2af24-107">Tato zpráva neplatné pro tento stav je a transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="2af24-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2af24-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="2af24-108">Troubleshooting</span></span>  
 <span data-ttu-id="2af24-109">Tato chyba může indiate, že trvalého účastníka (včetně podřízených TransactionManagers) došlo k zotavení z chyby, ale je jistí výstup transakce a požádat o jeho stav.</span><span class="sxs-lookup"><span data-stu-id="2af24-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af24-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2af24-110">See Also</span></span>  
 [<span data-ttu-id="2af24-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="2af24-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2af24-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="2af24-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2af24-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="2af24-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
