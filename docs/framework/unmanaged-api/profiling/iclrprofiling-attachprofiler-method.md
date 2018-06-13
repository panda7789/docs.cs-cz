---
title: ICLRProfiling::AttachProfiler – metoda
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52e3498b54f90e7d9d1d1d79ae0817cca511af4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459502"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler – metoda
Připojí zadaný profileru zadaný procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProfileeProcessID`  
 [v] ID procesu procesu, ke které je třeba připojit profileru. Na 64bitový počítač, musí odpovídat počtu bitů PROFILOVANÉHO proces počtu bitů aktivační proces, který volá `AttachProfiler`. Pokud uživatelský účet, pod které `AttachProfiler` nazývá oprávněními pro správu, tento cílový proces může být jakýkoli proces v systému. Tento Cílový proces, jinak hodnota musí být vlastníkem stejným uživatelským účtem.  
  
 `dwMillisecondsMax`  
 [v] Doba trvání (v milisekundách) pro `AttachProfiler` k dokončení. Proces aktivace by měla předávat vypršení časového limitu, který se označuje dostačující pro konkrétní profileru k dokončení inicializace.  
  
 `pClsidProfiler`  
 [v] Ukazatel na CLSID profilování má být načten. Proces aktivace můžete znovu použít tuto paměť po `AttachProfiler` vrátí.  
  
 `wszProfilerPath`  
 [v] Úplná cesta k souboru DLL profileru má být načten. Tento řetězec musí obsahovat více než 260 znaků, včetně ukončení hodnotu null. Pokud `wszProfilerPath` má hodnotu null nebo prázdný řetězec, modul CLR (CLR) pokusí najít umístění souboru DLL profileru tak, že vyhledá v registru CLSID který `pClsidProfiler` odkazuje na.  
  
 `pvClientData`  
 [v] Ukazatel na data mají být předány profileru pomocí [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda. Proces aktivace můžete znovu použít tuto paměť po `AttachProfiler` vrátí. Pokud `pvClientData` má hodnotu null, `cbClientData` musí být 0 (nula).  
  
 `cbClientData`  
 [v] Velikost v bajtech dat, která `pvClientData` odkazuje na.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující hodnoty HRESULT.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zadaný profileru se úspěšně připojil k tento cílový proces.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Již existuje profileru aktivních nebo připojení pro tento cílový proces.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Zadaný profileru nepodporuje připojení. Proces aktivace se pokusit připojit různé profileru.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nelze požadavek přílohu profileru, protože verze tento cílový proces je kompatibilní s aktuální proces, který volá `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Uživatel aktivační proces nemá přístup k tento cílový proces.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Uživatel proces aktivace nemá oprávnění potřebná k připojení profileru k dané Cílový proces. V protokolu událostí aplikace může obsahovat další informace.|  
|CORPROF_E_IPC_FAILED|Došlo k chybě při komunikaci s tento cílový proces. K tomu běžně dochází, pokud byl tento cílový proces vypíná.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Tento Cílový proces neexistuje nebo není spuštěná CLR, který podporuje přílohy. To může znamenat, že modulu CLR byl odpojen od volání metody výčtu modulu runtime.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Časový limit platnost bez začátku načíst profileru. Může pokus zopakovat operaci připojení. Časové limity dojde finalizační metodu v tento cílový proces běží po dobu delší než hodnota časového limitu.|  
|E_INVALIDARG|Jeden nebo více parametrů obsahuje neplatnou hodnotu.|  
|E_FAIL|Některé jiné, neurčené chybě.|  
|Další kódy chyb|Pokud profileru [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) HRESULT označující selhání, vrátí metoda `AttachProfiler` vrátí to stejné HRESULT. V takovém případě E_NOTIMPL jsou převedeny na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="memory-management"></a>Správa paměti  
 Při ochraně s konvence COM, volající `AttachProfiler` (například kód aktivační události vytvořené profileru vývojáře) zodpovídá za přidělování a zrušte přidělování paměti pro data, `pvClientData` parametr odkazuje na. Když spustí modulu CLR `AttachProfiler` volání, která umožňuje kopírování paměti, `pvClientData` odkazuje na a odesílá na tento cílový proces. Když CLR uvnitř tento cílový proces obdrží vlastní kopii `pvClientData` bloku, pak předá bloku profileru prostřednictvím `InitializeForAttach` metoda a pak zruší přidělení jeho kopii `pvClientData` bloku z tento cílový proces.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
