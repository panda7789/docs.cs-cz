---
title: ICorProfilerFunctionControl::SetCodegenFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992079"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags – metoda
Nastaví jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) překompilovány výčtu pro generování kódu pro ovládací prvek just-in-time (JIT) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [in] Jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
 Získá instanci tohoto rozhraní prostřednictvím profiler [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání. `SetCodegenFlags` Umožňuje profileru k řízení generování kódu pro rekompilované funkce. Stejně jako všechny ostatní JIT rekompilace parametry, příznaky generování kódu platí pro všechny instance funkce.  
  
 Kompilátor JIT bere v úvahu tyto příznaky kompilace, společně s další příznaky specifikovat z jiných zdrojů, při kompilaci funkce.  Další zdroje patří ladicí program, globální příznaky nastavením při spuštění pomocí profileru pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) – metoda (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS`) a profileru [ Icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětného volání.  Kompilátor JIT dává přednost před ke zdroji, který vyžaduje minimální množství optimalizace.  Například, pokud profiler Určuje `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) zpětné volání, vkládání je stále zakázáno.  Podobně pokud profiler neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags`, ale pak zakáže vkládání pomocí [icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětné volání, vkládání je zakázaná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerFunctionControl – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
