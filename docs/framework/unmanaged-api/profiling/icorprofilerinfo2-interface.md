---
title: "ICorProfilerInfo2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2
helpviewer_keywords: ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47ce316765117108da8e26d92a72febd0efb124d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 – rozhraní
Poskytuje metody, které profilery kódu se používají ke komunikaci s modul common language runtime (CLR) k řízení sledování událostí a informace o požadavku. `ICorProfilerInfo2` Rozhraní je rozšířením [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní. To znamená nabízí nové metody, které jsou podporovány v rozhraní .NET Framework verze 2.0 a novějších verzích.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Provede zásobník zadaný vlákno tak, aby odesílaly spravované volání rámce profileru.|  
|[EnumModuleFrozenObjects – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Získá enumerátor, který umožňuje iteraci přes ukotvené objekty v zadaný modul.|  
|[GetAppDomainStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Získá adresu domény statické pole určená aplikace, které je v oboru domény zadané aplikace.|  
|[GetArrayObjectInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Získá podrobné informace o objektu array.|  
|[GetBoxClassLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Získá informace o rozložení třídy pro zadanou hodnotu typ, který je zabalená.|  
|[GetClassFromTokenAndTypeArgs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Získá `ClassID` typu pomocí tokenu Zadaná metadata a `ClassID` argumentů hodnoty libovolného typu.|  
|[GetClassIDInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Získá nadřazený modul zadaný obecná třída token metadat pro třídu, `ClassID` ze své nadřízené třídy a `ClassID` pro každý typ argumentu, pokud existuje, třídy.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Získá informace o rozložení, v paměti pro pole definovaná v zadané třídě. To znamená tato metoda získá posun třída polí.|  
|[GetCodeInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Získá rozsah nativní kód spojený se zadaným `FunctionID`.|  
|[GetContextStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Získá adresu zadaný kontext statické pole, které je v rozsahu zadaný kontext.|  
|[GetFunctionFromTokenAndTypeArgs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Získá `FunctionID` funkce pomocí Zadaná metadata token, který obsahuje třídy, a `ClassID` argumentů hodnoty libovolného typu.|  
|[GetFunctionInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Získá nadřazené třídy, metadata token a `ClassID` každý typ argumentu, pokud je k dispozici funkce.|  
|[GetGenerationBounds – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Získá oblasti paměti (segmenty halda), které tvoří generace uvolňování paměti haldy.|  
|[GetNotifiedExceptionClauseInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Získá nativní adresy a rámce informace pro klauzuli výjimky (`catch`/`finally`/`filter`), má být spuštěna, nebo byla právě spuštěna.|  
|[GetObjectGeneration – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Získá segment haldě, které obsahuje zadaný objekt.|  
|[GetRVAStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Získá adresu zadaný relativní virtuální adresy (RVA)-statické pole.|  
|[GetStaticFieldInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Získá obor, ve které je v zadaném poli statické.|  
|[GetStringLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Získá informace o rozložení objektu řetězce.|  
|[GetThreadAppDomain – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Získá ID domény aplikace, ve kterém je zadaný vlákno aktuálně provádění kódu.|  
|[GetThreadStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Získá adresu zadaného pole statické přístup z více vláken, který je v rozsahu zadaný vlákno.|  
|[SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Určuje implementované profileru funkce k volání na "zadejte", "nechte" a "tailcall" háky spravovaných funkcí.|  
  
## <a name="remarks"></a>Poznámky  
 Profileru volá metodu `ICorProfilerInfo2` rozhraní ke komunikaci s CLR řízení sledování událostí a vyžádání informací.  
  
 Metody `ICorProfilerInfo2` rozhraní jsou implementované pomocí modelu podprocesy modulu CLR. Každá metoda vrátí HRESULT indikující úspěch nebo selhání. Seznam možných návratové kódy naleznete v souboru CorError.h.  
  
 Modul CLR předá `ICorProfilerInfo2` rozhraní pro každý kód profileru při inicializaci pomocí okna profilování implementace [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Kód profileru potom může volat metody `ICorProfilerInfo2` rozhraní pro získání informací o spravovaného kódu vykonáván pod kontrolou modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
