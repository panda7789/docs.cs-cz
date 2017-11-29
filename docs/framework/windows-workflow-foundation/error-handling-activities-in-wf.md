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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcb006f649fe0d2a92b4c789c435ba33916d140f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-activities-in-wf"></a>Zpracování chyb aktivity v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]poskytuje několik poskytované systémem aktivity pro implementace zpracování chyb a obnovení. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Výjimky](../../../docs/framework/windows-workflow-foundation/exceptions.md).  
  
## <a name="error-handling-activities"></a>Chyba zpracování aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Znovu vyvolá poslední výjimky z uvnitř `TryCatch` aktivity.|  
|<xref:System.Activities.Statements.Throw>|Vyvolá výjimku.|  
|<xref:System.Activities.Statements.TryCatch>|Zpracovávání výjimek v jazyce implementuje.|
