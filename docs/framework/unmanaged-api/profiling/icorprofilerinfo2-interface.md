---
title: ICorProfilerInfo2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4623fecd210ac716824fdc5fede99ec40145e8d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498866"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 – rozhraní
Poskytuje metody, které profilery kódu se používají ke komunikaci s common language runtime (CLR), která řídí sledování událostí a informace o žádostech. `ICorProfilerInfo2` Rozhraní je rozšířením [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní. To znamená, že poskytuje nové metody, které jsou podporovány v rozhraní .NET Framework verze 2.0 a novějších verzích.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Prochází zásobník zadaného vlákna informuje spravovaných volání snímků profileru.|  
|[EnumModuleFrozenObjects – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Získá enumerátor, který umožní iterace přes zmrazené objekty v zadaném modulu.|  
|[GetAppDomainStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Získá adresu zadané aplikace domény statická pole, které je v oboru zadanou doménu aplikace.|  
|[GetArrayObjectInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Získá podrobnosti o objektu array.|  
|[GetBoxClassLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Získá informace o rozložení třídy pro zadaného typu hodnoty, který je v poli.|  
|[GetClassFromTokenAndTypeArgs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Získá `ClassID` typu pomocí tokenu Zadaná metadata a `ClassID` hodnot ve všech argumentů typu.|  
|[GetClassIDInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Získá nadřazený modul zadané obecné třídy tokenu metadat pro třídu, `ClassID` své nadřazené třídy a `ClassID` pro každý typ argumentu, pokud jsou k dispozici třídy.|  
|[GetClassLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Získá informace o rozvržení, v paměti, pole definovaná pomocí dané třídy. To znamená tato metoda načte posuny polí třídy.|  
|[GetCodeInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Získá rozsah nativního kódu přidružený k zadanému `FunctionID`.|  
|[GetContextStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Získá adresu zadané kontextu statická pole, které je v rámci zadaného kontextu.|  
|[GetFunctionFromTokenAndTypeArgs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Získá `FunctionID` funkce s použitím Zadaná metadata token, který obsahuje třídy, a `ClassID` hodnot ve všech argumentů typu.|  
|[GetFunctionInfo2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Získá na nadřazenou třídu tokenu metadat a `ClassID` každý typ argumentu, pokud jsou k dispozici funkce.|  
|[GetGenerationBounds – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Získá oblastí paměti (segmenty halda), které tvoří generací haldě uvolňování.|  
|[GetNotifiedExceptionClauseInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Získá nativní rámce informace o adrese a pro klauzuli výjimky (`catch`/`finally`/`filter`), který má být spuštěna, nebo jenom nebyly spuštěny.|  
|[GetObjectGeneration – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Získá segment, který obsahuje zadaný objekt haldy.|  
|[GetRVAStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Získá adresu zadané relativní virtuální adresu (RVA) – statické pole.|  
|[GetStaticFieldInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Získá obor, ve kterém je statická pole zadané.|  
|[GetStringLayout – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Získá informace o rozložení objektu string.|  
|[GetThreadAppDomain – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Získá ID domény aplikace 00Z zadaného vlákna právě spouští kód.|  
|[GetThreadStaticAddress – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Získá adresu zadané pole vlákna, která je v rámci zadaného vlákna.|  
|[SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Určuje profiler implementovat funkce dřív říkalo "zadejte", "ponechte" a "tailcall" háky spravované funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Profiler volá metodu v `ICorProfilerInfo2` rozhraní ke komunikaci s modulem CLR řídit sledování událostí a žádost o informace.  
  
 Metody `ICorProfilerInfo2` rozhraní jsou implementovány modulem CLR pomocí modelu volných vláken. Každá metoda vrátí HRESULT indikuje úspěch nebo selhání. Seznam možných návratové kódy naleznete v souboru CorError.h.  
  
 Předá CLR `ICorProfilerInfo2` rozhraní pro každou pomocí profileru provádění profiler kódu během inicializace [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler kódu provést zavoláním metody `ICorProfilerInfo2` rozhraní pro získání informací o spravovaném kódu se spouští v ovládacím prvku modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
