---
title: "Profilace globálních statických funkcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4da4509a6e8b87490cee076b403f3fa525de91e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-global-static-functions"></a>Profilace globálních statických funkcí
Tato část popisuje nespravovaných funkcí rozhraní API, které používá profilaci API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funkce profilace rozhraní .NET framework verze 1  
 [Functionenter – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Upozorní profileru, že se ovládací prvek předán do funkce. Zastaralé v rozhraní .NET Framework 2.0.  
  
 [Functionleave – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Upozorní profileru, že funkce je se vraťte na volajícího. Zastaralé v rozhraní .NET Framework 2.0.  
  
 [Functiontailcall – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce. Zastaralé v rozhraní .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funkce profilace rozhraní .NET framework verze 2  
 [Functionidmapper – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Profileru upozorní, že daným identifikátorem funkce může namapovat na alternativní ID, které má být používány [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětných volání pro tuto funkci. Taky umožňuje profileru indikující, zda chce dostávat zpětných volání pro tuto funkci  
  
 [Functionenter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Profileru upozorní, že ovládací prvek je předávána funkci a poskytuje informace o zásobníku argumenty rámec a funkce. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Functionleave2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Profileru upozorní, že funkce je vrátit volajícímu a poskytuje informace o zásobník rámec a funkce návratovou hodnotu. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Functiontailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Profileru upozorní, že aktuálně prováděné funkce provede volání funkce tail do jiné funkce a poskytuje informace o rámce zásobníku. Zastaralé v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Stacksnapshotcallback – funkce](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Poskytuje informace o každé spravované rámečkem a každé spuštění nespravované rámce v zásobníku při procházení zásobníku, který je inicializován nástrojem profileru [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda.  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funkce profilace rozhraní .NET framework verze 4  
 [Functionidmapper2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Profileru upozorní, že daným identifikátorem funkce může namapovat na alternativní ID, které má být používány [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zpětných volání pro tuto funkci. Taky umožňuje profileru indikující, zda chce dostávat zpětných volání pro tuto funkci.  
  
 `FunctionIDMapper2`rozšiřuje [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) fungovat s `clientData` parametr, který profilery může použít k rozlišení mezi moduly runtime.  
  
 [Functionenter3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Upozorní profileru, že se ovládací prvek předán do funkce.  
  
 [Functionenter3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Profileru upozorní, že se ovládací prvek předán do funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctionenter3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) k načtení argumentů rámec a funkce zásobníku.  
  
 [Functionleave3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Upozorní profileru, že se vrací ovládací prvek z funkce.  
  
 [Functionleave3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Profileru upozorní, že se vrací ovládací prvek z funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctionleave3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) načíst rámce zásobníku a návratovou hodnotu.  
  
 [Functiontailcall3 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Upozorní profileru, že aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce.  
  
 [Functiontailcall3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Upozorní profileru, který aktuálně prováděné funkce se chystá provést volání funkce tail do jiné funkce a poskytuje popisovač, který se dá předat do [icorprofilerinfo3::getfunctiontailcall3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) načíst rámce zásobníku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilace výčtů](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
