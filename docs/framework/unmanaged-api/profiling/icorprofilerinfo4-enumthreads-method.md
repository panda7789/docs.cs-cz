---
title: ICorProfilerInfo4::EnumThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502805"
---
# <a name="icorprofilerinfo4enumthreads-method"></a>ICorProfilerInfo4::EnumThreads – metoda
Vrátí enumerátor, který poskytuje metody pro sekvenční iteraci v kolekci všech spravovaných vláken v profilované procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 mimo Ukazatel na rozhraní [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerThreadEnum – rozhraní](icorprofilerthreadenum-interface.md)
- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
