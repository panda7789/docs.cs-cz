---
title: FunctionTailcall3WithInfo – funkce
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4c3487f39d4f4c667ec9eb4705e17ccf29d9a4c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490382"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo – funkce
Oznámí profileru, který aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který lze předat [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) načíst rámec zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionIDOrClientID`  
 [in] Identifikátor aktuálně prováděné funkci, která se chystá provést tail volání.  
  
 `eltInfo`  
 [in] Neprůhledný popisovač, který představuje informace o daném zásobníku. Tento popisovač je platný pouze během zpětného volání, který je předán.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionTailcall3WithInfo` Metoda zpětného volání oznámí profileru a funkce jsou volány umožňuje profileru používat [icorprofilerinfo3::getfunctiontailcall3info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) ke kontrole rámce zásobníku. Přístup k informacím rámce zásobníku, `COR_PRF_ENABLE_FRAME_INFO` příznak musí být nastavena. Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí, a pak používat [icorprofilerinfo3::setenterleavefunctionhooks3withinfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci vašeho implementace této funkce.  
  
 `FunctionTailcall3WithInfo` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
-   Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
 Provádění `FunctionTailcall3WithInfo` by neměla blokovat, protože způsobí zpoždění uvolnění paměti. Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti. Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionTailcall3WithInfo` vrátí.  
  
 Functiontailcall3withinfo – funkce také, nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
