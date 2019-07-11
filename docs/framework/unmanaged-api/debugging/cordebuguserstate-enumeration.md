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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fbbb3f924f610b604586dca78cab344217b544
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739460"
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
|`USER_SUSPEND_REQUESTED`|Se požaduje pozastavení vlákna.|  
|`USER_BACKGROUND`|Vlákno je spuštěno na pozadí.|  
|`USER_UNSTARTED`|Vlákno není spuštěna.|  
|`USER_STOPPED`|Vlákno bylo ukončeno.|  
|`USER_WAIT_SLEEP_JOIN`|Vlákno čeká další vlákno k dokončení úkolu.|  
|`USER_SUSPENDED`|Vlákno bylo pozastaveno.|  
|`USER_UNSAFE_POINT`|Vlákno je nebezpečné okamžiku. Vlákno je v bodě provádění kde blokuje uvolňování paměti.<br /><br /> Ladění události může být z něj odešle nebezpečné body, ale nebezpečné okamžiku pozastavení vlákna budou velmi pravděpodobné, že k vzájemnému zablokování až se obnoví vlákno. Bezpečné a unsafe body jsou určeny just-in-time (JIT) a implementaci kolekce uvolnění paměti.|  
|`USER_THREADPOOL`|Vlákno je z fondu podprocesů.|  
  
## <a name="remarks"></a>Poznámky  
 Stav uživatele vlákna je stav, který má vlákna prozkoumá ladicí program. Vlákno může mít kombinaci stavů uživatele.  
  
 Použití [icordebugthread::getuserstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metody k získání stavu uživatele vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
