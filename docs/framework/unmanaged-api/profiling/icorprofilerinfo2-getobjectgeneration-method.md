---
title: "ICorProfilerInfo2::GetObjectGeneration – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a28b5e031ae39be39cc00740043b86ef2a9854
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a>ICorProfilerInfo2::GetObjectGeneration – metoda
Získá segment haldě, které obsahuje zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a>Parametry  
 `objectId`  
 [v] ID objektu.  
  
 `range`  
 [out] Ukazatel [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktura, která popisuje rozsah (to znamená, blok) paměti v generaci, kterou právě probíhá uvolňování paměti. Tento rozsah obsahuje zadaný objekt.  
  
## <a name="remarks"></a>Poznámky  
 `GetObjectGeneration` Může být volána metoda žádné profileru zpětné volání, za předpokladu, že není v průběhu uvolňování paměti. To znamená, může být volána z jakékoli zpětného volání kromě těch, které se vyskytnou mezi [icorprofilercallback2::garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
