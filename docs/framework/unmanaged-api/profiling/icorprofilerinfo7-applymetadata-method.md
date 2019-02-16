---
title: ICorProfilerInfo7::ApplyMetaData Method
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5caf7b5e24ac5e583420b45c563f53b8988f1e00
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332660"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData Method
[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]  
  
 Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Identifikátor modulu, jehož metadat byl změněn.  
  
## <a name="remarks"></a>Poznámky  
 Pokud dojde ke změně metadat po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětné volání, musí volat tuto metodu před použitím novými metadaty.  
  
 `ApplyMetaData` podporuje pouze přidávání následující typy metadat:  
  
-   `AssemblyRef` záznamy, které vytvoříte pomocí volání [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). Metoda.  
  
-   `TypeRef` záznamy, které vytvoříte pomocí volání [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.  
  
-   `TypeSpec` záznamy, které vytvoříte pomocí volání [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.  
  
-   `MemberRef` záznamy, které vytvoříte pomocí volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.  
  
-   `MemberSpec` záznamy, které vytvoříte pomocí volání [imetadataemit2::definemethodspec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.  
  
-   `UserString` záznamy, které vytvoříte pomocí volání [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.  

Od verze .NET Core 3.0, `ApplyMetaData` také podporuje následující typy:

- `TypeDef` záznamy, které vytvoříte pomocí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metody.

- `MethodDef` záznamy, které vytvoříte pomocí volání [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metody. Ale přidávání virtuální metody k existujícímu typu se nepodporuje. Virtuální metody, je třeba přidat před [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
