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
ms.openlocfilehash: 29aecd530d18b931420467e9127bcbf96d3a4a5f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866761"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler – metoda
Připojí zadaný profiler k zadanému procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parametry

- `dwProfileeProcessID`

  \[v] ID procesu procesu, ke kterému se má profiler připojit. Na 64ovém počítači musí bitová verze procesu profilace odpovídat bitová verze procesu triggeru, který volá `AttachProfiler`. Pokud uživatelský účet, pod kterým je `AttachProfiler` volána, má oprávnění správce, cílový proces může být jakýkoli proces v systému. Jinak cílový proces musí být vlastněn stejným uživatelským účtem.

- `dwMillisecondsMax`

  \[] časový interval pro `AttachProfiler` dokončení v milisekundách. Proces triggeru by měl projít časovým limitem, který by měl být dostatečný pro konkrétní profiler k dokončení inicializace.
  
- `pClsidProfiler`

  \[in] ukazatel na identifikátor CLSID profileru, který se má načíst. Proces triggeru může tuto paměť znovu použít po vrácení `AttachProfiler`.

- `wszProfilerPath`

  \[v] Úplná cesta k souboru DLL profileru, který se má načíst. Řetězec nesmí obsahovat více než 260 znaků, včetně ukončovacího znaku null. Pokud je `wszProfilerPath` null nebo prázdný řetězec, modul CLR (Common Language Runtime) se pokusí najít umístění souboru DLL profileru hledáním v registru pro identifikátor CLSID, na který `pClsidProfiler` odkazuje.

- `pvClientData`

  \[in] ukazatel na data, která mají být předána do profileru metodou [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) . Proces triggeru může tuto paměť znovu použít po vrácení `AttachProfiler`. Pokud je `pvClientData` null, `cbClientData` musí mít hodnotu 0 (nula).

- `cbClientData`

  \[] velikost dat, která `pvClientData` odkazuje, v bajtech.

## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující hodnoty HRESULT.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zadaný Profiler byl úspěšně připojen k cílovému procesu.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Profiler je již aktivní nebo se k cílovému procesu připojuje.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Zadaný Profiler nepodporuje přílohu. Aktivační proces se může pokusit připojit k jinému profileru.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nelze vyžádat přílohu profileru, protože verze cílového procesu není kompatibilní s aktuálním procesem, který volá `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Uživatel procesu triggeru nemá přístup k cílovému procesu.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Uživatel procesu triggeru nemá oprávnění potřebná k připojení profileru k danému cílovému procesu. Protokol událostí aplikace může obsahovat více informací.|  
|CORPROF_E_IPC_FAILED|Při komunikaci s cílovým procesem došlo k chybě. K tomu obvykle dochází v případě, že se cílový proces vypíná.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Cílový proces neexistuje nebo není spuštěn modul CLR, který podporuje přílohu. To může znamenat, že modul CLR byl uvolněn od volání metody výčtu modulu runtime.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Vypršel časový limit bez začátku načítání profileru. Operaci připojení můžete opakovat. K vypršení časového limitu dojde, když finalizační metoda v cílovém procesu běží delší dobu než hodnota časového limitu.|  
|E_INVALIDARG|Jeden nebo více parametrů má neplatné hodnoty.|  
|E_FAIL|V některých případech došlo k nespecifikovanému selhání.|  
|Další kódy chyb|Pokud metoda [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) profileru vrátí hodnotu HRESULT, která indikuje chybu, `AttachProfiler` vrátí stejnou hodnotu HRESULT. V tomto případě je E_NOTIMPL převést na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="memory-management"></a>Správa paměti  
 V souladu s konvencemi COM je volajícím `AttachProfiler` (například aktivační kód vytvořený vývojářem profileru) zodpovědný za přidělení a zrušení přidělení paměti pro data, na která parametr `pvClientData` odkazuje. Když CLR spustí `AttachProfiler` volání, vytvoří kopii paměti, na kterou `pvClientData` odkazuje, a přenáší ji do cílového procesu. Když CLR uvnitř cílového procesu obdrží svou vlastní kopii `pvClientData` bloku, předá blok do profileru prostřednictvím metody `InitializeForAttach` a poté zruší přidělení kopie `pvClientData` bloku z cílového procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
