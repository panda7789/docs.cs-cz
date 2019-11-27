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
ms.openlocfilehash: 6d8b408675127cde399a8346f2b9734a0e038cb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427140"
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
 Když dojde k přechodu, Profiler obdrží zpětné volání [ICorProfilerCallback:: ManagedToUnmanagedTransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) nebo [ICorProfilerCallback:: UnmanagedToManagedTransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) , které poskytuje hodnotu výčtu `COR_PRF_TRANSITION_REASON` k označení důvodu přechodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
