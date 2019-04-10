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
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211436"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl – rozhraní
Poskytuje metody, které umožňují profileru kód ke komunikaci s common language runtime (CLR) k řízení, jak by měl kompilátor JIT generování kódu při opětovné kompilaci konkrétní metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetCodegenFlags – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Nastaví jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) překompilovány výčtu pro generování kódu pro ovládací prvek just-in-time (JIT) funkce.|  
|[SetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Nahrazuje tělo Common Intermediate Language (CIL) metody.|  
|[SetILInstrumentedCodeMap – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Common Intermediate Language (CIL).|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerFunctionControl` Rozhraní poskytuje metody pro řízení generování kódu pro jedinou překompilovanou funkci. Získá instanci tohoto rozhraní prostřednictvím profiler [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání. Každá instance `ICorProfilerFunctionControl` řídí všechny instance funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
