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
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500556"
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

  \[v] ID procesu procesu, ke kterému se má profiler připojit. Na 64ovém počítači musí bitová verze procesu profilace odpovídat bitová verze procesu triggeru, který volá `AttachProfiler` . Pokud uživatelský účet, pod kterým `AttachProfiler` je volána oprávnění správce, může být cílovým procesem v systému. Jinak cílový proces musí být vlastněn stejným uživatelským účtem.

- `dwMillisecondsMax`

  \[in] doba trvání (v milisekundách), po `AttachProfiler` kterou se má dokončit. Proces triggeru by měl projít časovým limitem, který by měl být dostatečný pro konkrétní profiler k dokončení inicializace.
  
- `pClsidProfiler`

  \[in] ukazatel na identifikátor CLSID profileru, který má být načten. Proces triggeru může po vrácení znovu použít tuto paměť `AttachProfiler` .

- `wszProfilerPath`

  \[v] Úplná cesta k souboru DLL profileru, který se má načíst. Řetězec nesmí obsahovat více než 260 znaků, včetně ukončovacího znaku null. Pokud `wszProfilerPath` je hodnota null nebo prázdný řetězec, modul CLR (Common Language Runtime) se pokusí najít umístění souboru DLL profileru hledáním v registru pro identifikátor CLSID, `pClsidProfiler` na který odkazuje.

- `pvClientData`

  \[v] ukazatel na data, která mají být předána do profileru metodou [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) . Proces triggeru může po vrácení znovu použít tuto paměť `AttachProfiler` . Pokud `pvClientData` má hodnotu null, `cbClientData` musí mít hodnotu 0 (nula).

- `cbClientData`

  \[in] velikost dat, na která odkazuje, v bajtech `pvClientData` .

## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující hodnoty HRESULT.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Zadaný Profiler byl úspěšně připojen k cílovému procesu.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Profiler je již aktivní nebo se k cílovému procesu připojuje.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Zadaný Profiler nepodporuje přílohu. Aktivační proces se může pokusit připojit k jinému profileru.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nelze vyžádat přílohu profileru, protože verze cílového procesu není kompatibilní s aktuálním procesem, který volá `AttachProfiler` .|  
|HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)|Uživatel procesu triggeru nemá přístup k cílovému procesu.|  
|HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)|Uživatel procesu triggeru nemá oprávnění potřebná k připojení profileru k danému cílovému procesu. Protokol událostí aplikace může obsahovat více informací.|  
|CORPROF_E_IPC_FAILED|Při komunikaci s cílovým procesem došlo k chybě. K tomu obvykle dochází v případě, že se cílový proces vypíná.|  
|HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)|Cílový proces neexistuje nebo není spuštěn modul CLR, který podporuje přílohu. To může znamenat, že modul CLR byl uvolněn od volání metody výčtu modulu runtime.|  
|HRESULT_FROM_WIN32 (ERROR_TIMEOUT)|Vypršel časový limit bez začátku načítání profileru. Operaci připojení můžete opakovat. K vypršení časového limitu dojde, když finalizační metoda v cílovém procesu běží delší dobu než hodnota časového limitu.|  
|E_INVALIDARG|Jeden nebo více parametrů má neplatné hodnoty.|  
|E_FAIL|V některých případech došlo k nespecifikovanému selhání.|  
|Další kódy chyb|Pokud metoda [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) profileru vrátí hodnotu HRESULT, která označuje selhání, `AttachProfiler` vrátí stejnou hodnotu HRESULT. V tomto případě je E_NOTIMPL převést na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="memory-management"></a>Správa paměti  
 V souladu s konvencemi COM je volajícím `AttachProfiler` (například kód triggeru vytvořený vývojářem profileru) zodpovědný za přidělení a zrušení přidělení paměti pro data, `pvClientData` na která parametr odkazuje. Když CLR spustí `AttachProfiler` volání, vytvoří kopii paměti, která `pvClientData` odkazuje na a přenáší ji do cílového procesu. Když CLR uvnitř cílového procesu obdrží svou vlastní kopii `pvClientData` bloku, předá ho do profileru prostřednictvím `InitializeForAttach` metody a pak zruší přidělení kopie `pvClientData` bloku z cílového procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
