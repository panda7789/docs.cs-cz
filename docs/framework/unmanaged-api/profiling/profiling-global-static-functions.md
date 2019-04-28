---
title: Profilace globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bb5d93c91de857ebbee63009cad73fba7e1d284
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758246"
---
# <a name="profiling-global-static-functions"></a>Profilace globálních statických funkcí
Tato část popisuje nespravované funkce rozhraní API, které používá profilování API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funkce profilování rozhraní .NET framework verze 1  
 [FunctionEnter – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Oznámí profileru, že se ovládací prvek předán funkci. Zastaralé v rozhraní .NET Framework 2.0.  
  
 [FunctionLeave – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Oznámí profileru, že funkce se chystá vrácení volajícímu. Zastaralé v rozhraní .NET Framework 2.0.  
  
 [FunctionTailcall – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Oznámí profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce. Zastaralé v rozhraní .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funkce profilování rozhraní .NET framework verze 2  
 [FunctionIDMapper – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětná volání pro tuto funkci. Také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci  
  
 [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Profiler upozorní, že ovládací prvek je předáván funkci a poskytuje informace o zásobníku rámce a funkce argumenty. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionLeave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Profiler upozorní, že funkce je vracet volajícímu a poskytuje informace o zásobníku rámce a funkce návratová hodnota. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Profiler upozorní, že aktuálně prováděné funkci je provést volání funkce tail do jiné funkce a poskytuje informace o zásobníku. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StackSnapshotCallback – funkce](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Poskytuje informace o každý spravovaný rámec a každé spuštění nespravované rámce v zásobníku během procházení zásobníku, která inicializuje profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funkce profilování rozhraní .NET framework verze 4  
 [FunctionIDMapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zpětná volání pro tuto funkci. také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci.  
  
 `FunctionIDMapper2` rozšiřuje [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) pracovat `clientData` parametr, který profilovací programy mohou použít k rozlišení mezi moduly runtime.  
  
 [FunctionEnter3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Oznámí profileru, že se ovládací prvek předán funkci.  
  
 [FunctionEnter3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Oznámí profileru, že ovládací prvek je předáván funkci a poskytuje popisovač, který může být předán [icorprofilerinfo3::getfunctionenter3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) načíst zásobník snímků a funkce argumenty.  
  
 [FunctionLeave3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Oznámí profileru, že se řízení vrací z funkce.  
  
 [FunctionLeave3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Profiler upozorní, že ovládací prvek se vrací z funkce a poskytuje popisovač, který může být předán [icorprofilerinfo3::getfunctionleave3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) načíst rámec zásobníku a návratovou hodnotu.  
  
 [FunctionTailcall3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Oznámí profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.  
  
 [FunctionTailcall3WithInfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Oznámí profileru, který aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který může být předán [icorprofilerinfo3::getfunctiontailcall3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) načíst rámec zásobníku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
