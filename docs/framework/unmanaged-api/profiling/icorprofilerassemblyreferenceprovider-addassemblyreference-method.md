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
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866725"
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
 Profiler volá tuto metodu pro každé cílové sestavení, které plánuje odkaz ze sestavení zadaného v argumentu `wszAssemblyPath` volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) . Objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) je předán zpětnému volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) profileru spolu s cestou a názvem sestavení v argumentu `wszAssemblyPath`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerAssemblyReferenceProvider – rozhraní](icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences – metoda](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished – metoda](icorprofilercallback-moduleloadfinished-method.md)
