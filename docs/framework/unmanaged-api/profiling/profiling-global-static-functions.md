---
title: Profilace globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447432"
---
# <a name="profiling-global-static-functions"></a>Profilace globálních statických funkcí
Tato část popisuje nespravované funkce rozhraní API, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funkce profilování pro .NET Framework verze 1  
 [FunctionEnter – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci. Zastaralé v .NET Framework 2,0.  
  
 [FunctionLeave – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Upozorní profileru, že se chystá návrat funkce k volajícímu. Zastaralé v .NET Framework 2,0.  
  
 [FunctionTailcall – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce. Zastaralé v .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funkce profilace .NET Framework verze 2  
 [FunctionIDMapper – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)a [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) pro danou funkci. Také umožňuje profileru označit, zda chce přijímat zpětná volání pro tuto funkci.  
  
 [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci a poskytuje informace o bloku zásobníku a argumentech funkce. Zastaralé v .NET Framework 4.  
  
 [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce. Zastaralé v .NET Framework 4.  
  
 [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje informace o bloku zásobníku. Zastaralé v .NET Framework 4.  
  
 [StackSnapshotCallback – funkce](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funkce profilování pro .NET Framework verze 4  
 [FunctionIDMapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) pro danou funkci. Také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
 `FunctionIDMapper2` rozšiřuje funkci [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) s parametrem `clientData`, které profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.  
  
 [FunctionEnter3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci.  
  
 [FunctionEnter3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionEnter3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) za účelem načtení rámce zásobníku a argumentů funkce.  
  
 [FunctionLeave3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Upozorní profiler, že se vrací řízení z funkce.  
  
 [FunctionLeave3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionLeave3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) , aby získal rámec zásobníku a vrácenou hodnotu.  
  
 [FunctionTailcall3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.  
  
 [FunctionTailcall3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionTailcall3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) , aby mohl načíst rámec zásobníku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
