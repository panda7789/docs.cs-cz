---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 2325e3034dbf00441e587017affa65b80821fbb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128752"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Informuje modul CLR (Common Language Runtime) s odkazem na sestavení, který Profiler plánuje přidat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pAssemblyRefInfo  
 Ukazatel na strukturu [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) , která poskytuje CLR informace o odkazech na sestavení, které by měly být zváženy při provádění procházení ukončení odkazu na sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Profiler volá tuto metodu pro každé cílové sestavení, které plánuje odkaz ze sestavení zadaného v argumentu `wszAssemblyPath` volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) . Objekt rozhraní [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) je předán zpětnému volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) profileru spolu s cestou a názvem sestavení v argumentu `wszAssemblyPath`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
