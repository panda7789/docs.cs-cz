---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594358"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="9f107-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="9f107-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="9f107-103">Stavový počítač pro zařazení účastníka vstoupil do stavu dokončeno.</span><span class="sxs-lookup"><span data-stu-id="9f107-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f107-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9f107-104">Description</span></span>  
 <span data-ttu-id="9f107-105">Sledováno, když je dokončeno zpracování 2PC podřízeného účastníka.</span><span class="sxs-lookup"><span data-stu-id="9f107-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="9f107-106">Výsledek zařazení lze potvrdit nebo zrušit.</span><span class="sxs-lookup"><span data-stu-id="9f107-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="9f107-107">Je také sledováno, pokud některý účastník hlasy při přípravě ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="9f107-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f107-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f107-108">See also</span></span>

- [<span data-ttu-id="9f107-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="9f107-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="9f107-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="9f107-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9f107-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="9f107-111">Administration and Diagnostics</span></span>](../index.md)
