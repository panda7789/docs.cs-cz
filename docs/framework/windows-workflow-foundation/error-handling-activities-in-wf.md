---
title: Zpracování chyb aktivit v WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774020"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="84fbe-102">Zpracování chyb aktivit v WF</span><span class="sxs-lookup"><span data-stu-id="84fbe-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="84fbe-103">poskytuje několik aktivit poskytované systémem pro implementaci zpracování chyb a obnovení.</span><span class="sxs-lookup"><span data-stu-id="84fbe-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="84fbe-104">Další informace najdete v tématu [výjimky](exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="84fbe-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="84fbe-105">Chyba zpracování aktivity</span><span class="sxs-lookup"><span data-stu-id="84fbe-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="84fbe-106">Znovu vyvolá poslední výjimka vyvolána v rámci `TryCatch` aktivity.</span><span class="sxs-lookup"><span data-stu-id="84fbe-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="84fbe-107">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="84fbe-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="84fbe-108">Implementuje zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="84fbe-108">Implements exception handling.</span></span>|
