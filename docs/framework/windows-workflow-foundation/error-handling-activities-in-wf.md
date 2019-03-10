---
title: Zpracování chyb aktivit v WF
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707674"
---
# <a name="error-handling-activities-in-wf"></a>Zpracování chyb aktivit v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] poskytuje několik aktivit poskytované systémem pro implementaci zpracování chyb a obnovení. Další informace najdete v tématu [výjimky](exceptions.md).  
  
## <a name="error-handling-activities"></a>Chyba zpracování aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Znovu vyvolá poslední výjimka vyvolána v rámci `TryCatch` aktivity.|  
|<xref:System.Activities.Statements.Throw>|Vyvolá výjimku.|  
|<xref:System.Activities.Statements.TryCatch>|Implementuje zpracování výjimek.|
