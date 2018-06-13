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
# <a name="error-handling-activities-in-wf"></a>Zpracování chyb aktivity v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení. Další informace najdete v tématu [výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).  
  
## <a name="error-handling-activities"></a>Chyba zpracování aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.|  
|<xref:System.Activities.Statements.Throw>|Vyvolá výjimku.|  
|<xref:System.Activities.Statements.TryCatch>|Zpracovávání výjimek v jazyce implementuje.|
