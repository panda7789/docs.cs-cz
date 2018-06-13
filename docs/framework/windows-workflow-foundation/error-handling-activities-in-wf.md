---
title: Zpracování chyb aktivity v WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 51431e367f0ec8874588a52cb4dbd76d714768fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512382"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="be447-102">Zpracování chyb aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="be447-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="be447-103"> poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení.</span><span class="sxs-lookup"><span data-stu-id="be447-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="be447-104">Další informace najdete v tématu [výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="be447-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="be447-105">Chyba zpracování aktivity</span><span class="sxs-lookup"><span data-stu-id="be447-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="be447-106">Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.</span><span class="sxs-lookup"><span data-stu-id="be447-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="be447-107">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="be447-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="be447-108">Zpracovávání výjimek v jazyce implementuje.</span><span class="sxs-lookup"><span data-stu-id="be447-108">Implements exception handling.</span></span>|
