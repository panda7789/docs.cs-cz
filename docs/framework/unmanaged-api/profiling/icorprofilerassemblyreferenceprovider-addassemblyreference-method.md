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
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500504"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Informuje modul CLR (Common Language Runtime) s odkazem na sestavení, který Profiler plánuje přidat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Parametry

- `pAssemblyRefInfo`

  Ukazatel na [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) strukturu, která poskytuje CLR s informacemi o odkazech na sestavení, které by měly vzít v úvahu při provádění procházení ukončení odkazu na sestavení.
  
## <a name="remarks"></a>Poznámky  
 Profiler volá tuto metodu pro každé cílové sestavení, které plánuje odkaz ze sestavení zadaného v `wszAssemblyPath` argumentu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) . Objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) je předán zpětnému volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) profileru spolu s cestou k sestavení a názvem v `wszAssemblyPath` argumentu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)
- [Metoda GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished – metoda](icorprofilercallback-moduleloadfinished-method.md)
