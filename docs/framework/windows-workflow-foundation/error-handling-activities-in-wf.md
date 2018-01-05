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
# <a name="error-handling-activities-in-wf"></a>Zpracování chyb aktivity v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).  
  
## <a name="error-handling-activities"></a>Chyba zpracování aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.|  
|<xref:System.Activities.Statements.Throw>|Vyvolá výjimku.|  
|<xref:System.Activities.Statements.TryCatch>|Zpracovávání výjimek v jazyce implementuje.|
