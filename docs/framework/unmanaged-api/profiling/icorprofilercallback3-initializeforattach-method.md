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
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439517"
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
 pro Ukazatel rozhraní pro rozhraní `ICorProfilerInfo*`.  
  
 `pvClientData`  
 pro Ukazatel na data předaná metodě [IClrProfiling:: AttachProfiler –](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) ve svém parametru `pvClientData`. Pokud má tento parametr hodnotu null, `cbClientData` bude 0 (nula). Modul CLR uvolní tuto paměť při návratu z `InitializeForAttach`.  
  
 `cbClientData`  
 pro Velikost dat, která `pvClientData` odkazuje, v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá `InitializeForAttach`, aby Profiler mohl podat možnost požádat o zpětná volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
