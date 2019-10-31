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
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099647"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS – výčet
Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Tento modul runtime má k odeslání událost spravovaného ladicího programu bez zachycení. V části poznámky najdete rozdíl mezi zachycenými a nezachycenými událostmi.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Spravovaná událost, která čeká na vyřízení, je <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavek.|  
  
## <a name="remarks"></a>Poznámky  
 Mezi zachycené události patří proces, aplikační doména, sestavení, modul a oznámení o vytvoření vlákna, které přinášejí ladicímu programu až do aktuálního stavu poté, co se připojí k procesu. Nezachycené události, které jsou označeny příznakem `CLR_DEBUGGING_MANAGED_EVENT_PENDING`, zahrnují všechny další události ladicího programu, například výjimky a oznámení o spravovaném ladění pomocníka (MDA).  
  
 Příznak `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` umožňuje modulu runtime rozlišovat ukončující výjimku a požadavek na připojení spravovaného ladicího programu, který lze zrušit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Metahost. idl, Metahost. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
- [Ladění](index.md)
