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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e1a95b3078f4a592e28e0deb9869fc520cde811d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779274"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach – metoda
Volána modulem common language runtime (CLR), která poskytující nástroji pro profilování příležitost k inicializaci svého stavu po operaci připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCorProfilerInfoUnk`  
 [in] Pro ukazatel rozhraní `ICorProfilerInfo*` rozhraní.  
  
 `pvClientData`  
 [in] Předat ukazatel na data [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metodu v jeho `pvClientData` parametru. Pokud má parametr hodnotu null, `cbClientData` 0 (nula). Modul CLR uvolnění tuto paměť návratu z `InitializeForAttach`.  
  
 `cbClientData`  
 [in] Velikost v bajtech, dat, která `pvClientData` odkazuje na.  
  
## <a name="remarks"></a>Poznámky  
 Volání CLR `InitializeForAttach` k poskytující nástroji pro profilování příležitost k žádosti o zpětných volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
