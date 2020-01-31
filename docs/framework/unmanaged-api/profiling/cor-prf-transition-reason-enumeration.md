---
title: COR_PRF_TRANSITION_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867043"
---
# <a name="cor_prf_transition_reason-enumeration"></a>COR_PRF_TRANSITION_REASON – výčet
Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|Přechod je způsoben voláním funkce.|  
|`COR_PRF_TRANSITION_RETURN`|Přechod je způsoben návratem z funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Když dojde k přechodu, Profiler obdrží zpětné volání [ICorProfilerCallback:: ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) nebo [ICorProfilerCallback:: UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) , které poskytuje hodnotu výčtu `COR_PRF_TRANSITION_REASON` k označení důvodu přechodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
