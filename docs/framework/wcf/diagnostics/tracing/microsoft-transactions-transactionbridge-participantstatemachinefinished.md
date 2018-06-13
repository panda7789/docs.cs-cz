---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 85b8cc4e5044cc7c87ea784e09c160cc527dddaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473529"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="53324-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="53324-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="53324-103">Stav stavového stroje pro zápis účastníka přešla do konečného stavu.</span><span class="sxs-lookup"><span data-stu-id="53324-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="53324-104">Popis</span><span class="sxs-lookup"><span data-stu-id="53324-104">Description</span></span>  
 <span data-ttu-id="53324-105">Sledovat po dokončení zpracování 2pc podřízené účastnické zařazení.</span><span class="sxs-lookup"><span data-stu-id="53324-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="53324-106">Výsledek pro zařazení může být potvrzené nebo přerušené.</span><span class="sxs-lookup"><span data-stu-id="53324-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="53324-107">Také trasovaný Pokud kterýkoli účastník hlasy během Příprava jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="53324-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53324-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="53324-108">See Also</span></span>  
 [<span data-ttu-id="53324-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="53324-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="53324-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="53324-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="53324-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="53324-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
