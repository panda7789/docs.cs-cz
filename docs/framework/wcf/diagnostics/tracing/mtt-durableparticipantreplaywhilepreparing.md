---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 3b51a100677221866186b2e24f34396c012d11c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603128"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="f5d9e-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="f5d9e-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="f5d9e-103">Služba protokolu WS-AT obdržela odpověď od trvalého účastníka, který neodpověděl na připravit.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="f5d9e-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5d9e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="f5d9e-105">Description</span></span>  
 <span data-ttu-id="f5d9e-106">Trasovaná, pokud se stále připravuje trvalého účastníka bylo přijato odpověď.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="f5d9e-107">Toto je neplatná zpráva pro tento stav a transakce bude přerušen.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f5d9e-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="f5d9e-108">Troubleshooting</span></span>  
 <span data-ttu-id="f5d9e-109">Tato chyba může indiate, trvalého účastníka (včetně podřízených TransactionManagers) se zotavil po selhání, i když je jistí, jaké výsledek transakce a požádat o jeho stav.</span><span class="sxs-lookup"><span data-stu-id="f5d9e-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d9e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5d9e-110">See also</span></span>
- [<span data-ttu-id="f5d9e-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="f5d9e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="f5d9e-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="f5d9e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f5d9e-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="f5d9e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
