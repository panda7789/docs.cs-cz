---
title: "ICorProfilerInfo3::RequestProfilerDetach – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 33a5c45bbb64029177a0a680243dd39a825683e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach – metoda
Dá pokyn modulu runtime odpojit profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwExpectedCompletionMilliseconds`  
 [v] Doba v milisekundách, modul CLR (CLR) má čekat před kontroluje, zda je bezpečné uvolnit profileru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Odpojení žádost je platná, a Postup odpojení teď budete pokračovat na jiné vlákno. Po dokončení plně odpojení `ProfilerDetachSucceeded` vygenerování události.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Profileru se nezdařilo [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) pokus pro [icorprofilercallback3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) rozhraní, které se musí implementovat pro podporu operace odpojení. Odpojit neproběhl pokus o.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Odpojení není možné, protože profileru nastavte neměnné příznaky při spuštění. Neproběhl pokus o odpojení; profileru je stále plně připojený.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Odpojení je obtížné, protože používá profileru instrumentovány kód Microsoft intermediate language (MSIL) nebo vložené `enter` / `leave` háky. Neproběhl pokus o odpojení; profileru je stále plně připojený.<br /><br /> **Poznámka:** Instrumentovány MSIL je kód je kód, který je poskytována profiler pomocí [setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metoda.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Modul runtime ještě nebyla inicializována ve spravované aplikaci. (To znamená, modul runtime nebyla úplným načtením) Tento kód chyby mohou být vráceny, když se v rámci zpětného volání profileru požaduje odpojení [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metoda.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach`byla volána v nepodporované čase. K tomu dojde, pokud je na spravované vlákno, ale nikoli z volání metody [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metoda nebo z [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody, které nemůžou tolerovat uvolnění paměti. Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Poznámky  
 Během procesu odpojení odpojit vlákno (vlákno vytvořené speciálně pro odpojení profileru) příležitostně kontroluje, zda mají všechna vlákna byl ukončen okna profilování kódu. Profileru by měl poskytovat odhad jak dlouho to má trvat prostřednictvím `dwExpectedCompletionMilliseconds` parametr. Je dobré hodnota použít typické množství času stráví profileru do žádného zadané `ICorProfilerCallback*` metoda; tato hodnota by neměla být nižší než polovinu maximální množství času profileru očekává, že tráví.  
  
 Odpojení vlákno používá `dwExpectedCompletionMilliseconds` rozhodnout, jak dlouho do režimu spánku před kontrola, zda kód zpětného volání profileru má byly odebrány vypnout všechny balíčky. I když podrobnosti o následujícím algoritmu může v budoucích verzích změnit modulu CLR, ilustruje jeden ze způsobů `dwExpectedCompletionMilliseconds` lze použít při určování, kdy je bezpečné uvolnit profileru. Vlákno odpojení nejprve v režimu spánku `dwExpectedCompletionMilliseconds` milisekundách. Pokud po probuzení z režimu spánku, modulu CLR zjistí, že profileru zpětného volání kód je stále přítomen, vlákno odpojení uspí znovu, tentokrát pro dvakrát `dwExpectedCompletionMilliseconds` milisekundách. Pokud po probuzení ze spánku tento druhý vlákno odpojení najde, že profileru zpětného volání kód je stále přítomen, uspí 10 minut před opětovnou kontrolu. Odpojení vlákno pokračuje spusťte opětovnou kontrolu každých 10 minut.  
  
 Pokud profileru Určuje `dwExpectedCompletionMilliseconds` jako 0 (nula), modul CLR používá výchozí hodnotu 5000, což znamená, že provede kontrolu po 5 sekund, po 10 sekundách, a potom každých 10 minut po tomto datu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
