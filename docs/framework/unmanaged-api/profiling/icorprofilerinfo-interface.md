---
title: ICorProfilerInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
ms.openlocfilehash: 0af990930e8c30307e9da3b586621ca8ddb95d0c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438745"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo – rozhraní
Poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí a informace o požadavcích.  
  
> [!NOTE]
> Každá metoda v rozhraní `ICorProfilerInfo` vrátí HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v tématu CorError. h.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicializuje podporu ladění v procesu. Tato metoda je zastaralá ve verzi .NET Framework 2,0.|  
|[EndInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Ukončí relaci ladění v procesu. Tato metoda je zastaralá ve verzi .NET Framework 2,0.|  
|[ForceGC – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Vynutí uvolňování paměti v modulu runtime.|  
|[GetAppDomainInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Načte informace o zadané doméně aplikace.|  
|[GetAssemblyInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Načte informace o zadaném sestavení.|  
|[GetClassFromObject – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Získá `ClassID`<br /><br /> objekt, který je dán `ObjectID`.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Získá ID třídy s ohledem na token metadat. Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte metodu [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .|  
|[GetClassIDInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Získá nadřazený modul a token metadat pro určenou třídu.|  
|[GetCodeInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Získá rozsah nativního kódu přidruženého k zadanému ID funkce. Tato metoda je zastaralá. Místo toho použijte metodu [ICorProfilerInfo2:: GetCodeInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) .|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Získá ID aktuálního vlákna, pokud se jedná o spravované vlákno.|  
|[GetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení události z CLR.|  
|[GetFunctionFromIP – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapuje ukazatel na instrukci spravovaného kódu na `FunctionID`.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Získá ID funkce. Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte metodu [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .|  
|[GetFunctionInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Získá nadřazenou třídu a token metadat pro určenou funkci.|  
|[GetHandleFromThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mapuje ID vlákna na popisovač vlákna Win32.|  
|[GetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Získá ukazatel na tělo metody v kódu jazyka MSIL (Microsoft Intermediate Language) od jejího záhlaví.|  
|[GetILFunctionBodyAllocator – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Získá rozhraní, které poskytuje metodu pro přidělení paměti, která se má použít pro odměnu těla metody v kódu jazyka MSIL.|  
|[GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Získá mapu z posunu MSIL k nativním posunům pro kód obsažený v zadané funkci.|  
|[GetInprocInspectionInterface – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Získá objekt, na který lze zadat dotaz na rozhraní ICorDebugProcess. Tato metoda je zastaralá ve verzi .NET Framework 2,0.|  
|[GetInprocInspectionIThisThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Získá objekt, který lze dotazovat pro rozhraní ICorDebugThread. Tato metoda je zastaralá ve verzi .NET Framework 2,0.|  
|[GetModuleInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Po předaném ID modulu vrátí název souboru modulu a ID nadřazeného sestavení modulu.|  
|[GetModuleMetaData – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Získá instanci rozhraní metadat, která se mapuje na určený modul.|  
|[GetObjectSize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Získá velikost zadaného objektu.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Získá identitu kontextu aktuálně přidruženou k zadanému vláknu.|  
|[GetThreadInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Získá aktuální identitu vlákna Win32 pro zadané vlákno.|  
|[GetTokenAndMetadataFromFunction – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Získá token metadat a instanci rozhraní metadat, které lze použít proti tokenu pro zadanou funkci.|  
|[IsArrayClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Určuje, zda je zadaná třída třídou Array.|  
|[SetEnterLeaveFunctionHooks – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Určuje funkce implementované profilerem, které mají být volány u funkcí "Enter", "opustit" a "Tailcall" u spravovaných funkcí.|  
|[SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení od CLR.|  
|[SetFunctionIDMapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru.|  
|[SetFunctionReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Není implementováno. Nepoužívejte.|  
|[SetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Nahradí tělo zadané funkce v zadaném modulu.|  
|[SetILInstrumentedCodeMap – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Určuje, jakým způsobem posune původní jazyk MSIL zadané funkce na nové posuny rozhraní MSIL upraveného profilerem funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Profiler volá metodu v rozhraní `ICorProfilerInfo` ke komunikaci s modulem CLR pro řízení událostí a informace o požadavcích.  
  
 Metody rozhraní `ICorProfilerInfo` jsou implementovány modulem CLR pomocí modelu s volnými vlákny. Každá metoda vrátí hodnotu HRESULT, aby označovala úspěch nebo neúspěch. Seznam možných návratových kódů naleznete v tématu CorError. h.  
  
 CLR projde pomocí implementace [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)v profileru rozhraní `ICorProfilerInfo` do každého profileru kódu během inicializace. Profiler kódu pak může volat metody rozhraní `ICorProfilerInfo`, aby bylo možné získat informace o spravovaném kódu spuštěném pod kontrolou CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
