---
title: CorDebugUserState – výčet
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d0394d511197c8d0aaa366ce7b791216a3d226bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120191"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState – výčet
Určuje stav uživatele vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Členové  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Bylo vyžádáno ukončení vlákna.|  
|`USER_SUSPEND_REQUESTED`|Bylo vyžádáno pozastavení vlákna.|  
|`USER_BACKGROUND`|Vlákno je spuštěno na pozadí.|  
|`USER_UNSTARTED`|Vlákno nezahájilo provádění.|  
|`USER_STOPPED`|Vlákno bylo ukončeno.|  
|`USER_WAIT_SLEEP_JOIN`|Vlákno čeká na dokončení úlohy jiným vláknem.|  
|`USER_SUSPENDED`|Vlákno bylo pozastaveno.|  
|`USER_UNSAFE_POINT`|Vlákno je v nebezpečném bodě. To znamená, že vlákno je v okamžiku spuštění, kde může blokovat uvolňování paměti.<br /><br /> Události ladění mohou být odesílány z nebezpečných bodů, ale pozastavení vlákna v nezabezpečeném bodě pravděpodobně způsobí zablokování až do obnovení vlákna. Bezpečné a nebezpečné body jsou určeny implementací JIT (just-in-time) a uvolňování paměti.|  
|`USER_THREADPOOL`|Vlákno je z fondu vláken.|  
  
## <a name="remarks"></a>Poznámky  
 Stav uživatele vlákna je stav, který vlákno má, když ho prohlíží ladicí program. Vlákno může obsahovat kombinaci stavů uživatele.  
  
 Pro načtení stavu uživatele vlákna použijte metodu [ICorDebugThread:: GetUserState –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
