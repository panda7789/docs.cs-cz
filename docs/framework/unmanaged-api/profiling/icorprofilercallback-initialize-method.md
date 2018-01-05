---
title: "ICorProfilerCallback::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a54ed382724b99fb4b2ae3a21d2d212379f55fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize – metoda
Volat za účelem inicializace profileru kód při každém spuštění nové aplikace běžné runtime (CLR) jazyk.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pICorProfilerInfoUnk`  
 [v](/cpp/atl/iunknown) rozhraní, které musí vyhledat profileru [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ukazatel rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 `Initialize` Volání je pouze možnost povolit (nebo zakázat) zpětná volání, které jsou neměnné. Jakmile povolíte zpětné volání pomocí `Initialize` volat, nelze zakázat, později pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Hodnota COR_PRF_MONITOR_IMMUTABLE [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet Určuje události, které jsou neměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
