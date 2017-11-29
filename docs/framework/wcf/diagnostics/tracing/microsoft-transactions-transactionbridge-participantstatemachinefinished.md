---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53ac142c8c7d8004020210ffb3c0dcb2355a5b61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="52d95-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="52d95-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="52d95-103">Stav stavového stroje pro zápis účastníka přešla do konečného stavu.</span><span class="sxs-lookup"><span data-stu-id="52d95-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="52d95-104">Popis</span><span class="sxs-lookup"><span data-stu-id="52d95-104">Description</span></span>  
 <span data-ttu-id="52d95-105">Sledovat po dokončení zpracování 2pc podřízené účastnické zařazení.</span><span class="sxs-lookup"><span data-stu-id="52d95-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="52d95-106">Výsledek pro zařazení může být potvrzené nebo přerušené.</span><span class="sxs-lookup"><span data-stu-id="52d95-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="52d95-107">Také trasovaný Pokud kterýkoli účastník hlasy během Příprava jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="52d95-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d95-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="52d95-108">See Also</span></span>  
 [<span data-ttu-id="52d95-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="52d95-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="52d95-110">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="52d95-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="52d95-111">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="52d95-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
