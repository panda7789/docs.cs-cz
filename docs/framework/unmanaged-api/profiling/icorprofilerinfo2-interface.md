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
ms.openlocfilehash: 23fd44a6865b0487296f3ade37c1219e8feba288
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862578"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 – rozhraní
Poskytuje metody, které profilery kódu používají ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích. Rozhraní `ICorProfilerInfo2` je rozšířením rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) . To znamená, že poskytuje nové metody podporované v .NET Framework verze 2,0 a novějších verzích.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DoStackSnapshot – metoda](icorprofilerinfo2-dostacksnapshot-method.md)|Provede vystavení zásobníku zadaného vlákna, aby se do profileru hlásily spravované rámce volání.|  
|[EnumModuleFrozenObjects – metoda](icorprofilerinfo2-enummodulefrozenobjects-method.md)|Získá enumerátor, který umožňuje iteraci přes zmrazené objekty v zadaném modulu.|  
|[GetAppDomainStaticAddress – metoda](icorprofilerinfo2-getappdomainstaticaddress-method.md)|Získá adresu zadaného pole domény aplikace (static), které je v oboru zadané domény aplikace.|  
|[GetArrayObjectInfo – metoda](icorprofilerinfo2-getarrayobjectinfo-method.md)|Získá podrobné informace o objektu Array.|  
|[GetBoxClassLayout – metoda](icorprofilerinfo2-getboxclasslayout-method.md)|Načte informace o rozložení třídy pro zadaný typ hodnoty, který je zabalený.|  
|[GetClassFromTokenAndTypeArgs – metoda](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Získá `ClassID` typu pomocí zadaného tokenu metadat a hodnot `ClassID` jakýchkoli argumentů typu.|  
|[GetClassIDInfo2 – metoda](icorprofilerinfo2-getclassidinfo2-method.md)|Získá nadřazený modul zadané obecné třídy, token metadat pro třídu, `ClassID` své nadřazené třídy a `ClassID` pro každý argument typu, pokud je k dispozici pro třídu.|  
|[GetClassLayout – metoda](icorprofilerinfo2-getclasslayout-method.md)|Načte informace o rozložení v paměti polí definovaných specifikovanou třídou. To znamená, že tato metoda získá posuny polí třídy.|  
|[GetCodeInfo2 – metoda](icorprofilerinfo2-getcodeinfo2-method.md)|Získá rozsahy nativního kódu přidruženého k zadané `FunctionID`.|  
|[GetContextStaticAddress – metoda](icorprofilerinfo2-getcontextstaticaddress-method.md)|Získá adresu zadaného kontextového a statického pole, které je v oboru zadaného kontextu.|  
|[GetFunctionFromTokenAndTypeArgs – metoda](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Získá `FunctionID` funkce pomocí zadaného tokenu metadat, obsahující třídy a hodnot `ClassID` jakýchkoli argumentů typu.|  
|[GetFunctionInfo2 – metoda](icorprofilerinfo2-getfunctioninfo2-method.md)|Získá nadřazenou třídu, token metadat a `ClassID` každého argumentu typu, pokud je k dispozici funkce.|  
|[GetGenerationBounds – metoda](icorprofilerinfo2-getgenerationbounds-method.md)|Získá oblasti paměti (segmenty haldy), které tvoří generace haldy uvolňování paměti.|  
|[GetNotifiedExceptionClauseInfo – metoda](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Získá nativní adresu a informace o snímku pro klauzuli Exception (`catch`/`finally`/`filter`), které mají být spuštěny nebo právě spuštěny.|  
|[GetObjectGeneration – metoda](icorprofilerinfo2-getobjectgeneration-method.md)|Načte segment haldy, která obsahuje zadaný objekt.|  
|[GetRVAStaticAddress – metoda](icorprofilerinfo2-getrvastaticaddress-method.md)|Získá adresu zadaného relativní virtuální adresy (RVA) – statické pole.|  
|[GetStaticFieldInfo – metoda](icorprofilerinfo2-getstaticfieldinfo-method.md)|Získá rozsah, ve kterém je zadané pole statické.|  
|[GetStringLayout – metoda](icorprofilerinfo2-getstringlayout-method.md)|Získá informace o rozložení objektu řetězce.|  
|[GetThreadAppDomain – metoda](icorprofilerinfo2-getthreadappdomain-method.md)|Získá ID domény aplikace, ve které zadané vlákno aktuálně spouští kód.|  
|[GetThreadStaticAddress – metoda](icorprofilerinfo2-getthreadstaticaddress-method.md)|Získá adresu zadaného pole statického vlákna, které je v rozsahu zadaného vlákna.|  
|[SetEnterLeaveFunctionHooks2 – metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Určuje funkce implementované profilerem, které mají být volány u funkcí "Enter", "opustit" a "Tailcall" u spravovaných funkcí.|  
  
## <a name="remarks"></a>Poznámky  
 Profiler volá metodu v rozhraní `ICorProfilerInfo2` ke komunikaci s modulem CLR pro řízení událostí a informace o požadavcích.  
  
 Metody rozhraní `ICorProfilerInfo2` jsou implementovány modulem CLR pomocí modelu s volnými vlákny. Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v souboru CorError. h.  
  
 Modul CLR předá do každého profileru kódu při inicializaci `ICorProfilerInfo2` rozhraní, a to pomocí implementace [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)v profileru. Profiler kódu pak může volat metody rozhraní `ICorProfilerInfo2`, aby bylo možné získat informace o spravovaném kódu spuštěném pod kontrolou CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
