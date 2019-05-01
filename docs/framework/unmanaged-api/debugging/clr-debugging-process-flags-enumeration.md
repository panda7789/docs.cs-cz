---
title: CLR_DEBUGGING_PROCESS_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996356"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS – výčet
Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
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
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Tento modul runtime dojde k události catch nahoru spravovanému ladicímu programu k odeslání. Rozdíl mezi událostmi catch nahoru a hned v části poznámky.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Je spravovaná událost, která čeká na vyřízení <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavku.|  
  
## <a name="remarks"></a>Poznámky  
 Zachytávání událostí zahrnují procesu, aplikační domény, sestavení, modulu a oznámení o vytvoření vlákna, přinášející ladicí program až do aktuálního stavu po má připojení k procesu. Non-catch-up události, které jsou označeny `CLR_DEBUGGING_MANAGED_EVENT_PENDING` příznak, zahrnují všechny další události ladicího programu, jako jsou například výjimky a spravovaného ladění (MDA) pomocníka s nastavením oznámení.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Příznak umožňuje modulu runtime rozlišovat mezi ukončující výjimce a žádost o připojení spravovaného ladicího programu, který může být zrušen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Metahost.idl, Metahost.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
