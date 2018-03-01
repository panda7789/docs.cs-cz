---
title: "ICorProfilerInfo – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 08852b10f59e9c400b60287d78c8eb8eed5f109f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo – rozhraní
Poskytuje metody pro použití profilery kódu ke komunikaci s modul CLR (CLR) k řízení sledování událostí a vyžádání informací.  
  
> [!NOTE]
>  Každá metoda v `ICorProfilerInfo` rozhraní vrátí HRESULT indikující úspěch nebo selhání. CorError.h najdete seznam možných návratové kódy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicializuje ladění podpory v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[EndInprocDebugging – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Ukončí relaci ladění v procesu. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[ForceGC – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Vynutí uvolňování do modulu runtime.|  
|[GetAppDomainInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Získá informace o doméně zadané aplikace.|  
|[GetAssemblyInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Získá informace o zadaném sestavení.|  
|[GetClassFromObject – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Získá `ClassID` ze<br /><br /> objekt, daný jeho `ObjectID`.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Získá ID třídy, zadaný token metadat. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [ICorProfilerInfo2::getclassfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metoda místo.|  
|[GetClassIDInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Získá nadřazený modulu a metadata token pro zadanou třídu.|  
|[GetCodeInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Získá rozsah nativní kód spojený s ID zadanou funkci. Tato metoda je zastaralá. Použití [ICorProfilerInfo2::getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Získá ID aktuálního vlákna, pokud je spravované vlákno.|  
|[GetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Získá aktuální kategorií událostí, pro které profileru chce dostávat oznámení událostí z modulu CLR.|  
|[GetFunctionFromIP – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapuje ukazatel instrukce spravovaného kódu `FunctionID`.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Získá ID funkce. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [ICorProfilerInfo2::getfunctionfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metoda místo.|  
|[GetFunctionInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Získá nadřazené třídy a metadata token pro zadanou funkci.|  
|[GetHandleFromThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mapuje ID vlákna popisovač podprocesu Win32.|  
|[GetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Získá ukazatel k tělu metody v kódu (MSIL intermediate language) společnosti Microsoft, začínající na jeho záhlaví.|  
|[GetILFunctionBodyAllocator – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Získá rozhraní, které poskytuje metodu pro přidělení paměti, který se má použít pro odkládací out těla metody v MSIL kódu.|  
|[GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Získá mapu z MSIL posuny na nativní posunutí pro kód obsažené v zadanou funkci.|  
|[GetInprocInspectionInterface – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Získá objekt, který může být dotazován pro ICorDebugProcess rozhraní. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[GetInprocInspectionIThisThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Získá objekt, který může být dotazován pro rozhraní ICorDebugThread. Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.|  
|[GetModuleInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Zadaný modul ID vrátí název souboru modulu a ID modulu nadřazené sestavení.|  
|[GetModuleMetaData – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Získá instanci rozhraní metadata, která se mapuje na zadaný modul.|  
|[GetObjectSize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Získá velikost zadaného objektu.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Získá kontext identity aktuálně přidružen zadaný vlákno.|  
|[GetThreadInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Získá aktuální vlákno identitu Win32 pro zadaný vlákno.|  
|[GetTokenAndMetadataFromFunction – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Získá token metadat a instance metadat rozhraní, které můžete použít u tokenu pro zadanou funkci.|  
|[IsArrayClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Určuje, zda je pro zadanou třídu třídu pole.|  
|[SetEnterLeaveFunctionHooks – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Určuje implementované profileru funkce k volání na "zadejte", "nechte" a "tailcall" háky spravovaných funkcí.|  
|[SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profileru chce dostávat oznámení z modulu CLR.|  
|[SetFunctionIDMapper – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu.|  
|[SetFunctionReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Není implementováno. Nepoužívejte.|  
|[SetILFunctionBody – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Nahradí text zadaná funkce v zadaný modul.|  
|[SetILInstrumentedCodeMap – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Určuje, jak posunutí původní MSIL zadaná funkce mapovány nové posunutí MSIL profileru-byla změněna funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Profileru volá metodu `ICorProfilerInfo` rozhraní ke komunikaci s CLR řízení sledování událostí a vyžádání informací.  
  
 Metody `ICorProfilerInfo` rozhraní jsou implementované pomocí modelu podprocesy modulu CLR. Každá metoda vrátí HRESULT indikující úspěch nebo selhání. CorError.h najdete seznam možných návratové kódy.  
  
 Prostřednictvím implementace okna profilování předá modulu CLR [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), `ICorProfilerInfo` rozhraní pro každý kód profileru během inicializace. Kód profileru potom může volat metody `ICorProfilerInfo` rozhraní pro získání informací o spravovaného kódu vykonáván pod kontrolou modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
