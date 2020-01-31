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
ms.openlocfilehash: c3642154ba5f9798f59ca8fc49cb848d7e2f73c7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862227"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 – rozhraní
Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) k řízení monitorování událostí a k vyžádání informací. Rozhraní `ICorProfilerInfo3` je rozšířením rozhraní [ICorProfilerInfo2](icorprofilerinfo2-interface.md) . Poskytuje nové metody podporované .NET Framework 4 a novějšími verzemi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumJITedFunctions – metoda](icorprofilerinfo3-enumjitedfunctions-method.md)|Vrátí enumerátor pro všechny dříve kompilované funkce JIT.|  
|[EnumModules – metoda](icorprofilerinfo3-enummodules-method.md)|Vrátí enumerátor, který poskytuje metody pro sekvenční iteraci pomocí kolekce spravovaných modulů, které jsou načteny do aplikace.|  
|[GetAppDomainsContainingModule – metoda](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Získá identifikátory domén aplikace, ve kterých byl daný modul načten.|  
|[GetFunctionEnter3Info – metoda](icorprofilerinfo3-getfunctionenter3info-method.md)|Poskytuje rámec zásobníku a informace o argumentu funkce, která je hlášena profileru funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) . lze ji volat pouze během zpětného volání `FunctionEnter3WithInfo`.|  
|[GetFunctionLeave3Info – metoda](icorprofilerinfo3-getfunctionleave3info-method.md)|Poskytuje rámec zásobníku a návratovou hodnotu funkce, která je hlášena profileru funkcí [FunctionLeave3WithInfo – Function](functionleave3withinfo-function.md) . lze ji volat pouze během zpětného volání `FunctionLeave3WithInfo`.|  
|[GetFunctionTailcall3Info – metoda](icorprofilerinfo3-getfunctiontailcall3info-method.md)|Poskytuje rámec zásobníku funkce, která je hlášena profileru funkcí [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) . lze ji volat pouze během zpětného volání `FunctionTailcall3WithInfo`.|  
|[GetModuleInfo2 – metoda](icorprofilerinfo3-getmoduleinfo2-method.md)|Po předaném ID modulu vrátí název souboru modulu, ID nadřazeného sestavení modulu a bitovou masku, která popisuje vlastnosti modulu.|  
|[GetRuntimeInformation – metoda](icorprofilerinfo3-getruntimeinformation-method.md)|Poskytuje informace o verzi modulu runtime, který je profilace.|  
|[GetStringLayout2 – metoda](icorprofilerinfo3-getstringlayout2-method.md)|Získá informace o rozložení objektu řetězce.|  
|[GetThreadStaticAddress2 – metoda](icorprofilerinfo3-getthreadstaticaddress2-method.md)|Získá adresu zadaného pole statického vlákna, které je v oboru zadaného vlákna a domény aplikace.|  
|[RequestProfilerDetach – metoda](icorprofilerinfo3-requestprofilerdetach-method.md)|Instruuje modul runtime o odpojení profileru.|  
|[SetEnterLeaveFunctionHooks3 – metoda](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Určuje funkce implementované profilerem, které budou volány ve funkcích [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md) .|  
|[SetEnterLeaveFunctionHooks3WithInfo – metoda](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Určuje funkce implementované profilerem, které budou volány na [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –ch](functiontailcall3withinfo-function.md) zapojování spravovaných funkcí.|  
|[SetFunctionIDMapper2 – metoda](icorprofilerinfo3-setfunctionidmapper2-method.md)|Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru. Tato metoda rozšiřuje [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) s parametrem, který profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR implementuje metody rozhraní `ICorProfilerInfo3` pomocí modelu s volnými vlákny. Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v souboru CorError. h.  
  
 Modul CLR předá do každého profileru kódu během inicializace rozhraní `ICorProfilerInfo3` pomocí implementace metody [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) nebo [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) v profileru. Profiler kódu pak může volat metody `ICorProfilerInfo3` pro získání informací o spravovaném kódu, který je prováděn pod kontrolou CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
