---
title: Zpracování chyb aktivity v WF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c0459dd562f6292a8fe9a42f8b1b48cd175516a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="0ccb2-102">Zpracování chyb aktivity v WF</span><span class="sxs-lookup"><span data-stu-id="0ccb2-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="0ccb2-103"> poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="0ccb2-104">Další informace najdete v tématu [výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0ccb2-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="0ccb2-105">Chyba zpracování aktivity</span><span class="sxs-lookup"><span data-stu-id="0ccb2-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="0ccb2-106">Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="0ccb2-107">Vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="0ccb2-108">Zpracovávání výjimek v jazyce implementuje.</span><span class="sxs-lookup"><span data-stu-id="0ccb2-108">Implements exception handling.</span></span>|
