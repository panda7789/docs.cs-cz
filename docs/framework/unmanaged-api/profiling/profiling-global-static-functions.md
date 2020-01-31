---
title: Profilace globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860863"
---
# <a name="profiling-global-static-functions"></a>Profilace globálních statických funkcí
Tato část popisuje nespravované funkce rozhraní API, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funkce profilování pro .NET Framework verze 1  
 [FunctionEnter – funkce](functionenter-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci. Zastaralé v .NET Framework 2,0.  
  
 [FunctionLeave – funkce](functionleave-function.md)  
 Upozorní profileru, že se chystá návrat funkce k volajícímu. Zastaralé v .NET Framework 2,0.  
  
 [FunctionTailcall – funkce](functiontailcall-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce. Zastaralé v .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funkce profilace .NET Framework verze 2  
 [FunctionIDMapper – funkce](functionidmapper-function.md)  
 Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které má být použito v zpětných voláních [FunctionEnter2](functionenter2-function.md), [FunctionLeave2 –](functionleave2-function.md)a [FunctionTailcall2 –](functiontailcall2-function.md) pro danou funkci. Také umožňuje profileru označit, zda chce přijímat zpětná volání pro tuto funkci.  
  
 [FunctionEnter2 – funkce](functionenter2-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci a poskytuje informace o bloku zásobníku a argumentech funkce. Zastaralé v .NET Framework 4.  
  
 [FunctionLeave2 – funkce](functionleave2-function.md)  
 Upozorní profileru, že se chystá návrat funkce k volajícímu a poskytuje informace o bloku zásobníku a návratové hodnotě funkce. Zastaralé v .NET Framework 4.  
  
 [FunctionTailcall2 – funkce](functiontailcall2-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje informace o bloku zásobníku. Zastaralé v .NET Framework 4.  
  
 [StackSnapshotCallback – funkce](stacksnapshotcallback-function.md)  
 Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funkce profilování pro .NET Framework verze 4  
 [FunctionIDMapper2 – funkce](functionidmapper2-function.md)  
 Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md), nebo[Functionenter3withinfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) pro danou funkci. Také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.  
  
 `FunctionIDMapper2` rozšiřuje funkci [FunctionIDMapper –](functionidmapper-function.md) s parametrem `clientData`, které profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.  
  
 [FunctionEnter3 – funkce](functionenter3-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci.  
  
 [FunctionEnter3WithInfo – funkce](functionenter3withinfo-function.md)  
 Upozorňuje profileru, že řízení je předáno funkci, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) za účelem načtení rámce zásobníku a argumentů funkce.  
  
 [FunctionLeave3 – funkce](functionleave3-function.md)  
 Upozorní profiler, že se vrací řízení z funkce.  
  
 [FunctionLeave3WithInfo – funkce](functionleave3withinfo-function.md)  
 Upozorní profiler, že je vrácen ovládací prvek z funkce, a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) , aby získal rámec zásobníku a vrácenou hodnotu.  
  
 [FunctionTailcall3 – funkce](functiontailcall3-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce.  
  
 [FunctionTailcall3WithInfo – funkce](functiontailcall3withinfo-function.md)  
 Upozorní profileru, že aktuálně vykonávaná funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který může být předán do [ICorProfilerInfo3:: GetFunctionTailcall3Info –](icorprofilerinfo3-getfunctiontailcall3info-method.md) , aby mohl načíst rámec zásobníku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](profiling-overview.md)  
  
 [Rozhraní pro profilaci](profiling-interfaces.md)  
  
 [Výčty pro profilaci](profiling-enumerations.md)  
  
 [Struktury pro profilaci](profiling-structures.md)
