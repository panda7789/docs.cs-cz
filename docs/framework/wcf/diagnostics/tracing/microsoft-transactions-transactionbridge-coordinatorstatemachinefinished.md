---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594410"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="a4486-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="a4486-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="a4486-103">Stavový počítač pro zařazení koordinátora přešel do stavu dokončeno.</span><span class="sxs-lookup"><span data-stu-id="a4486-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a4486-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a4486-104">Description</span></span>  
 <span data-ttu-id="a4486-105">Sledováno, když místní správce transakce považuje za dokončenou 2PC zpracování.</span><span class="sxs-lookup"><span data-stu-id="a4486-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="a4486-106">Výsledek zařazení se dá potvrdit nebo zrušit nebo zapomenout.</span><span class="sxs-lookup"><span data-stu-id="a4486-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="a4486-107">Je také sledováno, pokud má správce místní transakce hlasy ReadOnly během přípravy.</span><span class="sxs-lookup"><span data-stu-id="a4486-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4486-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4486-108">See also</span></span>

- [<span data-ttu-id="a4486-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="a4486-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="a4486-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a4486-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a4486-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="a4486-111">Administration and Diagnostics</span></span>](../index.md)
