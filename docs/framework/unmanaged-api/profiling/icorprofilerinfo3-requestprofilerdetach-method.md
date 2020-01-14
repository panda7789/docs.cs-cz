---
title: ICorProfilerInfo3::RequestProfilerDetach – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 226f24ad8f1636101b283c3cb6662905cbf7eebe
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938211"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach – metoda
Instruuje modul runtime o odpojení profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 pro Doba (v milisekundách), kterou modul CLR (Common Language Runtime) musí čekat před kontrolou, aby se zobrazilo, zda je bezpečné uvolnit Profiler.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Požadavek na odpojení je platný a Postup odpojení nyní pokračuje v jiném vlákně. Po úplném dokončení odpojení dojde k vystavení `ProfilerDetachSucceeded` události.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Profiler selhal při pokusu [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pro rozhraní [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) , které musí implementovat pro podporu operace odpojení. Nedošlo k pokusu o odpojení.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Odpojení není možné, protože při spuštění sada profileru nastavila neměnné příznaky. Nedošlo k pokusu o odpojení; Profiler je stále plně připojený.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Odpojení není možné, protože Profiler použil instrumentované kód jazyka MSIL (Microsoft Intermediate Language) nebo vložený `enter`/`leave` vidlice. Nedošlo k pokusu o odpojení; Profiler je stále plně připojený.<br /><br /> **Poznámka:** Instrumentovaná MSIL je kód, který poskytuje Profiler pomocí metody [SetILFunctionBody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) .|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Modul runtime ještě není ve spravované aplikaci inicializovaný. (To znamená, že modul runtime nebyl zcela načten.) Tento kód chyby může být vrácen v případě, že je vyžadováno odpojení v rámci metody [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání profileru.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` byla volána v nepodporovaném čase. K tomu dochází, pokud je metoda volána ve spravovaném vlákně, ale ne v rámci metody [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) nebo v rámci metody [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) , která nemůže tolerovat uvolňování paměti. Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Poznámky  
 Během procesu odpojení se vlákno odpojení (vlákno vytvořené speciálně pro odpojení profileru) občas kontroluje, jestli všechna vlákna ukončila kód profileru. Profiler by měl poskytnout odhad toho, jak dlouho by měl tento parametr `dwExpectedCompletionMilliseconds` trvat. Dobrá hodnota, která se má použít, je obvyklá doba, kterou Profiler stráví v rámci určité `ICorProfilerCallback*` metody; Tato hodnota by neměla být menší než polovina maximálního množství času, po který profiler očekává útratu.  
  
 Vlákno odpojení používá `dwExpectedCompletionMilliseconds` k rozhodnutí, jak dlouho se má přejít do režimu spánku před kontrolou, zda byl kód zpětného volání profileru vyjmut ze všech zásobníků. I když se podrobnosti o následujícím algoritmu mohou v budoucích vydáních modulu CLR změnit, ukazuje jeden způsob, jak `dwExpectedCompletionMilliseconds` lze použít při určování, kdy je bezpečné uvolnit Profiler. Odpojování vlákna se při prvním režimu spánku `dwExpectedCompletionMilliseconds` milisekund. Pokud po probuzení z režimu spánku modul CLR najde, že kód zpětného volání profileru stále existuje, dojde k opětovnému odpojení vlákna odpojit, tentokrát se dvěma časy `dwExpectedCompletionMilliseconds` milisekund. Pokud po probuzení z tohoto druhého režimu spánku najde odpojené vlákno, že kód zpětného volání profileru je stále přítomen, po dobu 10 minut přejde do režimu spánku. Vlákno odpojení pokračuje v kontrole každých 10 minut.  
  
 Pokud profiler určí `dwExpectedCompletionMilliseconds` jako 0 (nula), CLR použije výchozí hodnotu 5000, což znamená, že provede kontrolu za 5 sekund, znovu po 10 sekundách a pak každých 10 minut.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
