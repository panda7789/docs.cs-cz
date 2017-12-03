---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f99670d61df45edfef5350da080f12e892a0f74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="49af6-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="49af6-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="49af6-103">Stav stavového stroje pro zápis koordinátora má přešla do stavu dokončení.</span><span class="sxs-lookup"><span data-stu-id="49af6-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49af6-104">Popis</span><span class="sxs-lookup"><span data-stu-id="49af6-104">Description</span></span>  
 <span data-ttu-id="49af6-105">Sledovat, když místní správce transakcí dochází k závěru, že zápis nadřízená koordinátora je dokončená 2pc zpracování.</span><span class="sxs-lookup"><span data-stu-id="49af6-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="49af6-106">Výsledek pro zařazení může být potvrzení nebo bylo přerušeno nebo Forgotten.</span><span class="sxs-lookup"><span data-stu-id="49af6-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="49af6-107">Také trasovaný Pokud místní správce transakcí hlasy během Příprava jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="49af6-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49af6-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="49af6-108">See Also</span></span>  
 [<span data-ttu-id="49af6-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="49af6-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="49af6-110">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="49af6-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="49af6-111">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="49af6-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
