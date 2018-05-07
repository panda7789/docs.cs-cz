---
title: ICorProfilerFunctionControl – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0daf772702ada9d426b3da6913fff0186e33564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl – rozhraní
Poskytuje metody, které umožňují kódu profileru ke komunikaci s modul CLR (CLR) k řízení, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetCodegenFlags – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Nastaví jeden nebo více příznaků z [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu pro generování kódu ovládacího prvku pro v běhu (JIT) překompilovat funkce.|  
|[SetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Nahrazuje tělo Common Intermediate Language (CIL) metody.|  
|[SetILInstrumentedCodeMap – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapování Common mezilehlá jazyk (CIL).|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerFunctionControl` Rozhraní poskytuje metody pro generování kódu pro jedné Rekompilované funkce řízení. Získá instanci tohoto rozhraní prostřednictvím profileru [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání. Každá instance `ICorProfilerFunctionControl` všechny instance jednu funkci ovládací prvky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumJITedFunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
