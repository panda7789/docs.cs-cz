---
title: "CLR_DEBUGGING_PROCESS_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_PROCESS_FLAGS
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords: CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6d66f9a11f28ca572e0f1eddc74f3a5197a19d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS – výčet
Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Tento modul runtime má událostí catch až spravované ladicí program k odeslání. Naleznete v části poznámky o rozdíl mezi událostmi opravný a catch nahoru.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Spravované událost, která čeká na vyřízení je <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavku.|  
  
## <a name="remarks"></a>Poznámky  
 Zachytávání událostí zahrnují procesu, doménu aplikace, sestavení, modulu a oznámení vytvoření přístup z více vláken, která vrátí ladicího programu až do aktuálního stavu po má připojit k procesu. Události bez catch-up, která jsou zobrazena `CLR_DEBUGGING_MANAGED_EVENT_PENDING` příznak, zahrnují všechny ostatní události ladicí program, jako je například výjimky a spravovaného ladění (MDA) pomocníka oznámení.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Příznak umožňuje modulu runtime rozlišit mezi ukončující výjimce a požadavek na připojení spravované ladicí program, který může být zrušen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Metahost.idl, Metahost.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
