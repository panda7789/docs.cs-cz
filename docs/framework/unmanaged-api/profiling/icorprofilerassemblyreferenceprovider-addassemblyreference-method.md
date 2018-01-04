---
title: "ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location: mscorwks.dll
api_type: COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 292d814c1a3f66b415e9a7b6220d8ee921f6b949
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Informuje o odkaz na sestavení, který profileru přidat v common language runtime (CLR) [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pAssemblyRefInfo  
 Ukazatel [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) struktura, která poskytuje informace o odkaz na sestavení, který ho měli zvážit při procházení uzavření odkaz na sestavení modulu CLR.  
  
## <a name="remarks"></a>Poznámky  
 Profileru volá tuto metodu pro každý cíl sestavení se plánuje odkazovat z sestavení zadané v `wszAssemblyPath` argument [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání. [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní objekt předaný okna profilování [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání, cesta k sestavení a název v `wszAssemblyPath` argument.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerAssemblyReferenceProvider – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
