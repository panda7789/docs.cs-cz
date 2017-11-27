---
title: "ICorProfilerInfo7::ApplyMetaData – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorProfilerInfo7.ApplyMetaData
api_location: mscorwks.dll
api_type: COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3724555df58392e5ab59ccb4f52dd2de860b8d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData – metoda
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
 [v] Identifikátor modulu, jehož metadata byl změněn.  
  
## <a name="remarks"></a>Poznámky  
 Pokud po provedení změn metadat [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětné volání, musí volat tuto metodu před použitím novými metadaty.  
  
 `ApplyMetaData`podporuje se jenom přidávání následující typy metadat:  
  
-   `AssemblyRef`záznamy, které vytvoříte pomocí volání [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). Metoda.  
  
-   `TypeRef`záznamy, které vytvoříte pomocí volání [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metoda.  
  
-   `TypeSpec`záznamy, které vytvoříte pomocí volání [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metoda.  
  
-   `MemberRef`záznamy, které vytvoříte pomocí volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda.  
  
-   `MemberSpec`záznamy, které vytvoříte pomocí volání [imetadataemit2::definemethodspec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metoda.  
  
-   `UserString`záznamy, které vytvoříte pomocí volání [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo7 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
