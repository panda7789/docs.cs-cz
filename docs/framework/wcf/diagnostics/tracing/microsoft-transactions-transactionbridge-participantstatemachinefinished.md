---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 56eb40d4e8b2580ba094e67552872cf558c8a617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642292"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="826be-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="826be-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="826be-103">Stavový počítač pro zapsání účastníka přešla do konečného stavu.</span><span class="sxs-lookup"><span data-stu-id="826be-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="826be-104">Popis</span><span class="sxs-lookup"><span data-stu-id="826be-104">Description</span></span>  
 <span data-ttu-id="826be-105">Trasovaná po dokončení zpracování 2pc podřízené zapsání účastníka.</span><span class="sxs-lookup"><span data-stu-id="826be-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="826be-106">Výsledek pro zařazení může být potvrzeno nebo bylo přerušeno.</span><span class="sxs-lookup"><span data-stu-id="826be-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="826be-107">Také se trasován, pokud každý účastník hlasů jen pro čtení během přípravy.</span><span class="sxs-lookup"><span data-stu-id="826be-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826be-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="826be-108">See also</span></span>
- [<span data-ttu-id="826be-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="826be-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="826be-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="826be-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="826be-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="826be-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
