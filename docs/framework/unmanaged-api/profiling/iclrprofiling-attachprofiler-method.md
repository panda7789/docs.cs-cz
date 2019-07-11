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
ms.openlocfilehash: efc097fd9b4da668aafce90ce601a3143ea57dc7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763167"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler – metoda
Připojí zadaný profiler do určeného procesu.  
  
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
 `dwProfileeProcessID`  
 [in] Proces ID procesu, ke kterému by měl profiler připojen. Na 64bitovém počítači profilovaný proces bitové verze musí odpovídat počtu bitů aktivační proces, který volá `AttachProfiler`. Pokud uživatelský účet, pod kterým `AttachProfiler` nazývá má oprávnění správce, Cílový proces může být jakýkoli proces v systému. V opačném případě cílový proces musí být vlastněno stejným uživatelským účtem.  
  
 `dwMillisecondsMax`  
 [in] Doba trvání v milisekundách pro `AttachProfiler` dokončete. Aktivační proces by měla předat vypršení časového limitu, který je znám jako dostatečná pro konkrétní profiler dokončit jeho inicializaci.  
  
 `pClsidProfiler`  
 [in] Ukazatel na identifikátor CLSID profileru, který se má načíst. Aktivační proces můžete znovu použít tuto paměť po `AttachProfiler` vrátí.  
  
 `wszProfilerPath`  
 [in] Úplná cesta k souboru knihovny DLL profileru, který se má načíst. Tento řetězec může obsahovat více než 260 znaků včetně ukončovacího znaku null. Pokud `wszProfilerPath` má hodnotu null nebo prázdný řetězec, modul CLR (CLR) se pokusí najít vyhledáváním v registru CLSID umístění souboru knihovny DLL profileru, který `pClsidProfiler` odkazuje na.  
  
 `pvClientData`  
 [in] Ukazatel na data, která má být předán profileru pomocí [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metody. Aktivační proces můžete znovu použít tuto paměť po `AttachProfiler` vrátí. Pokud `pvClientData` má hodnotu null, `cbClientData` musí být 0 (nula).  
  
 `cbClientData`  
 [in] Velikost v bajtech, dat, která `pvClientData` odkazuje na.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující výsledky HRESULT.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Zadaný profiler byl úspěšně přiřazen do cílového procesu.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Už existuje profiler aktivní nebo připojení k cílovým procesem.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Zadaný profiler nepodporuje připojení. Aktivační proces může pokusit o připojení různých profileru.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Nemůže požádat o profileru přílohu, protože verze Cílový proces není kompatibilní s aktuální proces, který volá `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Uživatel aktivační proces nemá přístup do cílového procesu.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Uživatel aktivační proces nemá oprávnění potřebná pro připojení profileru k dané cílového procesu. V protokolu událostí aplikace může obsahovat další informace.|  
|CORPROF_E_IPC_FAILED|Došlo k chybě při komunikaci s cílovým procesem. Běžně se to stane, když Cílový proces se vypíná.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Cílový proces neexistuje nebo není spuštěn CLR, který podporuje přílohy. To může znamenat, že modul CLR byl odpojen od posledního volání enumerační metoda modulu runtime.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Bez začátek načíst profiler vypršel její časový limit. Můžete opakovat operaci připojení. Vypršení časového limitu dojde finalizační metody v cílovém procesu běží po dobu delší než hodnota časového limitu.|  
|E_INVALIDARG|Jeden nebo více parametrů obsahuje neplatnou hodnotu.|  
|E_FAIL|Došlo k selhání některých jiných, Neurčeno.|  
|Další kódy chyb|Pokud profiler [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) HRESULT označující selhání, vrátí metoda `AttachProfiler` vrátí to stejné HRESULT. V takovém případě E_NOTIMPL je převedena na CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="memory-management"></a>Správa paměti  
 V udržení s modelu COM konvence volající `AttachProfiler` (například aktivační kód vytvořené profilerem vývojáře) zodpovídá za přidělování a zrušení přidělení paměti pro data, která `pvClientData` parametr odkazuje na. Když modul CLR provede `AttachProfiler` volání, vytvoří kopii paměti, která `pvClientData` odkazuje na a odesílá do cílového procesu. Když do cílového procesu CLR obdrží vlastní kopii `pvClientData` bloku, předá bloku do profileru pomocí `InitializeForAttach` metoda a pak zruší přidělení jeho kopii `pvClientData` blok z cílového procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
