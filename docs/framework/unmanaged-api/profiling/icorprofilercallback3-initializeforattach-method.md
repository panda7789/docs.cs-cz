---
title: ICorProfilerCallback3::InitializeForAttach – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 9bff594d0307153fb468b28c1535977f06997748
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499711"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach – metoda
Volá se modulem CLR (Common Language Runtime), aby Profiler mohl po operaci připojení inicializovat svůj stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCorProfilerInfoUnk`  
 pro Ukazatel rozhraní pro `ICorProfilerInfo*` rozhraní.  
  
 `pvClientData`  
 pro Ukazatel na data předaná metodě [IClrProfiling:: AttachProfiler –](iclrprofiling-attachprofiler-method.md) v `pvClientData` parametru. Pokud má tento parametr hodnotu null, `cbClientData` bude 0 (nula). Modul CLR uvolní tuto paměť, když se vrátí z `InitializeForAttach` .  
  
 `cbClientData`  
 pro Velikost dat, která odkazuje na velikost (v bajtech) `pvClientData` .  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní CLR volá, `InitializeForAttach` aby Profiler mohl podat možnost požádat o zpětná volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
