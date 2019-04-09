---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: bffaed4976d82202eaea9ce50f6d389548fdabfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144822"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="fa829-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="fa829-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="fa829-103">Stavový počítač pro zapsání koordinátora zadal stav dokončeno.</span><span class="sxs-lookup"><span data-stu-id="fa829-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa829-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fa829-104">Description</span></span>  
 <span data-ttu-id="fa829-105">Trasovaná při místní správce transakcí se řídí zásadou, že zapsání koordinátora na dokonalá dokončil zpracování 2pc.</span><span class="sxs-lookup"><span data-stu-id="fa829-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="fa829-106">Výsledek pro zařazení může být potvrzeno nebo bylo přerušeno nebo zapomenuté.</span><span class="sxs-lookup"><span data-stu-id="fa829-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="fa829-107">Také trasován Pokud místní správce transakcí hlasů jen pro čtení během přípravy.</span><span class="sxs-lookup"><span data-stu-id="fa829-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa829-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa829-108">See also</span></span>

- [<span data-ttu-id="fa829-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="fa829-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fa829-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fa829-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fa829-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="fa829-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
