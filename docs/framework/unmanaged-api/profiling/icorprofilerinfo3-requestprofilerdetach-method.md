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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab203fc054298971fadfd9abe4e787844313898b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765335"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach – metoda
Dá pokyn modulu runtime-li odpojit profiler.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 [in] Doba v milisekundách, modul CLR (CLR) by měl čekat, než zkontroluje, jestli je bezpečný pro uvolnění profileru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Požadavek na odpojení je platný a odpojit proceduru teď budete pokračovat v jiném vlákně. Po odpojení plně dokončení, `ProfilerDetachSucceeded` vygenerování události.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Došlo k selhání profileru [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pokusí pro [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) rozhraní, které musí implementovat pro podporu operace odpojení. Odpojit se přeskočila.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Odpojení není možné, protože profiler nastavit příznaky neměnných při spuštění. Odpojení se přeskočila; stále plně je profiler připojen.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Odpojení je možné, protože profiler používá instrumentována kód Microsoft intermediate language (MSIL) nebo vložené `enter` / `leave` zavěšení. Odpojení se přeskočila; stále plně je profiler připojen.<br /><br /> **Poznámka:** Instrumentována jazyk MSIL je následně kód je kód, který je poskytován profileru pomocí [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Modul runtime dosud nebyla inicializována ve spravované aplikaci. (To znamená, modul runtime ještě není zavedený plně.) Tento kód chyby může být vrácena, pokud se požaduje odpojení uvnitř zpětného volání profileru [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metody.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` byla volána v nepodporované době. K tomu dojde, pokud je metoda volána na spravovaná vlákna, ale ne z [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) – metoda nebo v rámci [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metodu, která nejde tolerovat uvolňování paměti. Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Poznámky  
 Během odpojení procesu, odpojení vlákna (vlákno vytvořené speciálně pro odpojení profileru) příležitostně kontroluje, zda máte všechna vlákna byl ukončen profileru kód. Profiler by měla poskytnout odhad, jak dlouho by to mělo trvat až `dwExpectedCompletionMilliseconds` parametru. Je dobré hodnota použít typické množství času stráví profiler uvnitř každá `ICorProfilerCallback*` metoda; tato hodnota by neměla být menší než polovinu maximální množství času věnovat očekává, že profiler.  
  
 Odpojení vlákna používá `dwExpectedCompletionMilliseconds` rozhodnout, jak dlouho do režimu spánku před vrácením se změnami, zda kód zpětného volání profileru byly odebrány všechny balíčky. I když podrobnosti následující požadovaný algoritmus může v budoucích verzích změnit modulu CLR, ukazuje jeden ze způsobů `dwExpectedCompletionMilliseconds` se dá použít při určování, kdy je bezpečné uvolnění profileru. Odpojení vlákna nejprve uspí `dwExpectedCompletionMilliseconds` milisekund. Pokud po probuzení z režimu spánku, modul CLR zjistí, že kód zpětného volání profileru je stále přítomen, odpojení vlákna po prodlevě znovu, tentokrát pro dvakrát `dwExpectedCompletionMilliseconds` milisekund. Pokud po probuzení z režimu spánku tento druhý odpojení vlákna zjistí, že kód zpětného volání profileru je stále přítomen, je 10 minut uspí před opětovnou kontrolu. Odpojení vlákna i nadále spusťte opětovnou kontrolu každých 10 minut.  
  
 Pokud profiler Určuje `dwExpectedCompletionMilliseconds` jako 0 (nula), používá modul CLR výchozí hodnotu 5000, což znamená, že provede kontrolu po 5 sekund, znovu za 10 sekund, a pak každých 10 minut po tomto datu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
