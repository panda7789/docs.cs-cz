---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486773"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="df4ca-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="df4ca-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="df4ca-103">Služba protokolu WS-AT obdržela odpověď od trvalého účastníka, který neodpověděl na připravit.</span><span class="sxs-lookup"><span data-stu-id="df4ca-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="df4ca-104">V důsledku toho byla transakce přerušena.</span><span class="sxs-lookup"><span data-stu-id="df4ca-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="df4ca-105">Popis</span><span class="sxs-lookup"><span data-stu-id="df4ca-105">Description</span></span>  
 <span data-ttu-id="df4ca-106">Trasovaná, pokud se stále připravuje trvalého účastníka bylo přijato odpověď.</span><span class="sxs-lookup"><span data-stu-id="df4ca-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="df4ca-107">Toto je neplatná zpráva pro tento stav a transakce bude přerušen.</span><span class="sxs-lookup"><span data-stu-id="df4ca-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="df4ca-108">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="df4ca-108">Troubleshooting</span></span>

<span data-ttu-id="df4ca-109">Tato chyba může znamenat, že trvalého účastníka (včetně podřízených TransactionManagers) se zotavuje ze selhání; Nicméně je jistí, jaké výsledek transakce a požadavky její stav.</span><span class="sxs-lookup"><span data-stu-id="df4ca-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4ca-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df4ca-110">See also</span></span>

- [<span data-ttu-id="df4ca-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="df4ca-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="df4ca-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="df4ca-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="df4ca-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="df4ca-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
