---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: f5d74d73cc43b500d3920ca03905f4eb7543619a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075532"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="8209f-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="8209f-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="8209f-103">Služba protokolu WS-AT obdržela odpověď od trvalého účastníka, který neodpověděl na připravit.</span><span class="sxs-lookup"><span data-stu-id="8209f-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="8209f-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="8209f-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8209f-105">Popis</span><span class="sxs-lookup"><span data-stu-id="8209f-105">Description</span></span>  
 <span data-ttu-id="8209f-106">Trasovaná, pokud se stále připravuje trvalého účastníka bylo přijato odpověď.</span><span class="sxs-lookup"><span data-stu-id="8209f-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="8209f-107">Toto je neplatná zpráva pro tento stav a transakce bude přerušen.</span><span class="sxs-lookup"><span data-stu-id="8209f-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8209f-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="8209f-108">Troubleshooting</span></span>  
 <span data-ttu-id="8209f-109">Tato chyba může indiate, trvalého účastníka (včetně podřízených TransactionManagers) se zotavil po selhání, i když je jistí, jaké výsledek transakce a požádat o jeho stav.</span><span class="sxs-lookup"><span data-stu-id="8209f-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8209f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8209f-110">See also</span></span>

- [<span data-ttu-id="8209f-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="8209f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8209f-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8209f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8209f-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8209f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
