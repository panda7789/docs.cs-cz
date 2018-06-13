---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: abb6a81d22da3a35c754c5d1485c5d612c9cd1e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473130"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="96f19-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="96f19-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="96f19-103">Stav stavového stroje pro zápis koordinátora má přešla do stavu dokončení.</span><span class="sxs-lookup"><span data-stu-id="96f19-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="96f19-104">Popis</span><span class="sxs-lookup"><span data-stu-id="96f19-104">Description</span></span>  
 <span data-ttu-id="96f19-105">Sledovat, když místní správce transakcí dochází k závěru, že zápis nadřízená koordinátora je dokončená 2pc zpracování.</span><span class="sxs-lookup"><span data-stu-id="96f19-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="96f19-106">Výsledek pro zařazení může být potvrzení nebo bylo přerušeno nebo Forgotten.</span><span class="sxs-lookup"><span data-stu-id="96f19-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="96f19-107">Také trasovaný Pokud místní správce transakcí hlasy během Příprava jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="96f19-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f19-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="96f19-108">See Also</span></span>  
 [<span data-ttu-id="96f19-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="96f19-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="96f19-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="96f19-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="96f19-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="96f19-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
