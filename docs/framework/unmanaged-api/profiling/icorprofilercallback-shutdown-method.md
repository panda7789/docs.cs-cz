---
title: ICorProfilerCallback::Shutdown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192638"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown – metoda
Oznámí profileru, že se aplikace vypíná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Poznámky  
 Profiler kódu nelze bezpečně volat metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) rozhraní po `Shutdown` metoda je volána. Všechna volání do `ICorProfilerInfo` metody za následek nedefinované chování po `Shutdown` metoda vrátí hodnotu. Určité neměnné události může stále dojít po vypnutí; profiler byste měli věnovat pozornost k vrácení okamžitě, pokud k tomu dojde.  
  
 `Shutdown` Metoda bude volána pouze v případě, že spravovaná aplikace, která je právě profilována spuštěn jako spravovaný kód (to znamená, je spravovaný počáteční rámec v zásobníku proces). Pokud aplikace spustil jako nespravovaný kód, ale později vstupovat do spravovaného kódu, a tím vytvoření instance modulu common language runtime (CLR), pak `Shutdown` nebude volána. Pro tyto případy, by měl obsahovat profileru v jeho knihovně `DllMain` rutiny, které používají DLL_PROCESS_DETACH hodnota uvolněte veškeré prostředky a provádět čištění zpracování nad svými daty, jako je vyprazdňování trasování na disk a tak dále.  
  
 Obecně platí profiler musí zvládnout neočekávané vypnutí. Například může být proces zastavení na Win32 `TerminateProcess` – metoda (deklarované v Winbase.h). V jiných případech zastaví CLR bez doručováním zpráv řádné zničení pro ně určité spravovaná vlákna (vláken na pozadí).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
