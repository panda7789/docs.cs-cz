---
title: ICorProfilerInfo3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21c2352a40d46c80e46c10a3874f911be433f37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 – rozhraní
Poskytuje metody, které profilery kódu se používají ke komunikaci s modul CLR (CLR) k řízení sledování událostí a k požadavku na informace. `ICorProfilerInfo3` Rozhraní je rozšířením [ICorProfilerInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) rozhraní. Poskytuje nové metody v podporované [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] a novějších verzích.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumJITedFunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Vrátí enumerátor pro všechny dříve kompilována funkce.|  
|[EnumModules – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Vrátí enumerátor, který poskytuje metody pro postupně iteraci prostřednictvím kolekce spravované moduly, které jsou načteny do aplikace.|  
|[GetAppDomainsContainingModule – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Získá identifikátory aplikační domény, ve kterých byl načten daného modulu.|  
|[GetFunctionEnter3Info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Poskytuje informace zásobníku rámec a argument funkce, která je hlášena profileru pomocí [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce; lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.|  
|[GetFunctionLeave3Info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Poskytuje rámce zásobníku a návratové hodnoty funkce, která je hlášena profileru pomocí [functionleave3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce; lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.|  
|[GetFunctionTailcall3Info – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Poskytuje rámce zásobníku funkce, která je hlášena profileru pomocí [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkce; lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.|  
|[GetModuleInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Zadaný modul ID vrátí název souboru modulu, ID modulu nadřazené sestavení a bitová maska, která popisuje vlastnosti modulu.|  
|[GetRuntimeInformation – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Poskytuje informace o verzi o modul runtime, který je profilovaný.|  
|[GetStringLayout2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Získá informace o rozložení objektu řetězce.|  
|[GetThreadStaticAddress2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Získá adresu zadaného pole statické přístup z více vláken, který je v oboru zadaný vláken a domény aplikace.|  
|[RequestProfilerDetach – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Dá pokyn modulu runtime odpojit profileru.|  
|[SetEnterLeaveFunctionHooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Určuje implementované profileru funkce, které bude volána při [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funkce.|  
|[SetEnterLeaveFunctionHooks3WithInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Určuje implementované profileru funkce, které bude volána při [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) háky spravované funkce.|  
|[SetFunctionIDMapper2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu. Tato metoda rozšiřuje [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) s parametrem profilery může použít k rozlišení mezi moduly runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR implementuje metody `ICorProfilerInfo3` rozhraní pomocí modelu podprocesy. Každá metoda vrátí HRESULT indikující úspěch nebo selhání. Seznam možných návratové kódy naleznete v souboru CorError.h.  
  
 Modul CLR předá `ICorProfilerInfo3` pro každý kód profileru při inicializaci pomocí okna profilování implementace rozhraní [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) nebo [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda. Potom můžete volat kód profileru `ICorProfilerInfo3` metod k získání informací spravovaného kódu, která se spouští pod kontrolou modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
