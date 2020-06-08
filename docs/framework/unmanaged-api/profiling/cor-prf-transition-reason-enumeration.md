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
ms.openlocfilehash: e890c62a54654e86bb4a825613807efe142c8d5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500738"
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
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|Přechod je způsoben voláním funkce.|  
|`COR_PRF_TRANSITION_RETURN`|Přechod je způsoben návratem z funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Když dojde k přechodu, Profiler obdrží zpětné volání [ICorProfilerCallback:: ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) nebo [ICorProfilerCallback:: UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) , z nichž každá poskytuje hodnotu `COR_PRF_TRANSITION_REASON` výčtu k označení důvodu přechodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
