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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b979b5f4ee849b96cd29b6c8e2e6a8932e88c182
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201712"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo – rozhraní
Poskytuje metody pro použití u profilery kódu ke komunikaci s common language runtime (CLR) k řízení sledování událostí a žádost o informace.  
  
> [!NOTE]
>  Každé metodě v `ICorProfilerInfo` rozhraní vrátí HRESULT indikuje úspěch nebo selhání. Seznam možných návratové kódy naleznete v tématu CorError.h.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicializuje podporu ladění v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[EndInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Ukončí relaci ladění v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[ForceGC – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Vynutí uvolňování paměti ke kterým došlo v modulu runtime.|  
|[GetAppDomainInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Získá informace o zadanou doménu aplikace.|  
|[GetAssemblyInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Získá informace o zadané sestavení.|  
|[GetClassFromObject – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Získá `ClassID` z<br /><br /> objekt dle jeho `ObjectID`.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Získá ID třídy, zadaný token metadat. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metoda místo.|  
|[GetClassIDInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Získá nadřazený modulu a tokenem metadat pro zadanou třídu.|  
|[GetCodeInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Vrátí rozsah nativního kódu přidružené k ID zadanou funkci. Tato metoda je zastaralá. Použití [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Získá ID aktuálního vlákna, pokud je spravovaným vláknem.|  
|[GetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Získá aktuální kategorie událostí, pro které profileru chce obdržet oznámení událostí z modulu CLR.|  
|[GetFunctionFromIP – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapuje ukazatel instrukce spravovaného kódu `FunctionID`.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Získá ID funkce. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metoda místo.|  
|[GetFunctionInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Získá nadřazené třídu a metadata token pro zadanou funkci.|  
|[GetHandleFromThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mapuje ID vlákna na popisovač podprocesu Win32.|  
|[GetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Získá ukazatel do těla metody v kódu Microsoft intermediate language (MSIL) začínající na jeho záhlaví.|  
|[GetILFunctionBodyAllocator – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Získá rozhraní, které představuje způsob, jak přidělit paměť pro záměnu těla metody v kódu MSIL.|  
|[GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Získá mapování z posunů MSIL do nativních posunů pro kód obsažený v zadané funkce.|  
|[GetInprocInspectionInterface – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Získá objekt, který je možné zadávat dotazy pro icordebugprocess – rozhraní. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[GetInprocInspectionIThisThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Získá objekt, který je možné zadávat dotazy pro icordebugthread – rozhraní. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[GetModuleInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Dané ID modulu vrátí název souboru modulu a ID modulu nadřazené sestavení.|  
|[GetModuleMetaData – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Získá instanci rozhraní metadat, který se mapuje na zadaný modul.|  
|[GetObjectSize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Získá velikost zadaného objektu.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Získá kontext identity aktuálně přiřazen k zadané vlákno.|  
|[GetThreadInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Získá aktuální identitu vlákna Win32 pro zadaný podproces.|  
|[GetTokenAndMetadataFromFunction – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Získá token metadat a instance objektu metadat rozhraní, které můžete použít pro token pro zadanou funkci.|  
|[IsArrayClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Určuje, zda dané třídy je třída pole.|  
|[SetEnterLeaveFunctionHooks – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Určuje profiler implementovat funkce dřív říkalo "zadejte", "ponechte" a "tailcall" háky spravované funkce.|  
|[SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení z modulu CLR.|  
|[SetFunctionIDMapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Určuje funkci, která bude volána k mapování profiler implementovat `FunctionID` hodnoty pro alternativní hodnoty, které jsou předány do profileru funkce zachytávání vstupu/výstupu.|  
|[SetFunctionReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Není implementováno. Nepoužívejte.|  
|[SetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Nahrazuje tělo zadanou funkci v zadaném modulu.|  
|[SetILInstrumentedCodeMap – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Určuje, jak posunů MSIL původní zadaná funkce mapují na nové posunů MSIL profileru změnit funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Profiler volá metodu v `ICorProfilerInfo` rozhraní ke komunikaci s modulem CLR řídit sledování událostí a žádost o informace.  
  
 Metody `ICorProfilerInfo` rozhraní jsou implementovány modulem CLR pomocí modelu volných vláken. Každá metoda vrátí HRESULT indikuje úspěch nebo selhání. Seznam možných návratové kódy naleznete v tématu CorError.h.  
  
 Prostřednictvím implementace okna profilování předá CLR [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), `ICorProfilerInfo` rozhraní pro každou profileru kód během inicializace. Profiler kódu provést zavoláním metody `ICorProfilerInfo` rozhraní pro získání informací o spravovaném kódu se spouští v ovládacím prvku modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
