---
title: "Zpracování chyb aktivity v WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a868cd28823c3185d1297f7709dcfdc28a14a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="c72cb-102">Zpracování chyb aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="c72cb-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="c72cb-103">poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení.</span><span class="sxs-lookup"><span data-stu-id="c72cb-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="c72cb-104">[Výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c72cb-104"> [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="c72cb-105">Chyba zpracování aktivity</span><span class="sxs-lookup"><span data-stu-id="c72cb-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="c72cb-106">Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.</span><span class="sxs-lookup"><span data-stu-id="c72cb-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="c72cb-107">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="c72cb-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="c72cb-108">Zpracovávání výjimek v jazyce implementuje.</span><span class="sxs-lookup"><span data-stu-id="c72cb-108">Implements exception handling.</span></span>|
