---
title: "CorDebugUserState – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57fd9df27b1911c90bd11712b67e6e64588c2b5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState – výčet
Určuje stav uživatele vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`USER_STOP_REQUESTED`|Byla vyžádána ukončení vlákna.|  
|`USER_SUSPEND_REQUESTED`|Byla vyžádána pozastavení vlákno.|  
|`USER_BACKGROUND`|Vlákno je spuštěno na pozadí.|  
|`USER_UNSTARTED`|Vlákno nebyla spuštěna.|  
|`USER_STOPPED`|Vlákno byla ukončena.|  
|`USER_WAIT_SLEEP_JOIN`|Vlákno čeká další vlákno k dokončení úlohy.|  
|`USER_SUSPENDED`|Vlákno bylo pozastaveno.|  
|`USER_UNSAFE_POINT`|Vlákno je na bod unsafe. To znamená vlákno je na místo v provádění kde může toto blokování uvolňování paměti.<br /><br /> Ladění událostí může odeslat z bodů unsafe, ale pozastavení vlákna na bod unsafe velmi pravděpodobně zablokování způsobí dokud vlákno obnovení. Bezpečné a unsafe body jsou určeny v běhu (JIT) a implementaci kolekce paměti.|  
|`USER_THREADPOOL`|Vlákno je z fondu vláken.|  
  
## <a name="remarks"></a>Poznámky  
 Stav uživatele vlákno je stav, který má vlákno při prozkoumá ladicího programu. Vlákno může mít kombinaci stavů uživatele.  
  
 Použití [icordebugthread::getuserstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metoda pro načtení stavu uživatele vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
