---
title: ICorProfilerInfo2::DoStackSnapshot – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3a558ad6f87995d6c0a0d164cf96376fba12da4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485262"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot – metoda
Provede spravované rámce zásobníku pro zadaný podproces a odešle informace prostřednictvím zpětné volání profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `thread`  
 [in] ID cílového vlákna.  
  
 Předání hodnotou null v `thread` vrací snímek aktuální vlákno. Pokud `ThreadID` z různých vláken je předán, common language runtime (CLR) pozastaví bylo vlákno, provádí snímku a obnoví.  
  
 `callback`  
 [in] Ukazatel na implementaci [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) metodu, která je volána modulem CLR poskytnout informace pro každý spravovaný rámec a každé spuštění nespravované snímků profileru.  
  
 `StackSnapshotCallback` Metoda je implementováno tvůrci profileru.  
  
 `infoFlags`  
 [in] Hodnota [cor_prf_snapshot_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) výčet, který určuje množství dat, které mají být předány zpět pro každý snímek podle `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Ukazatel na data klienta, která je předána přímo `StackSnapshotCallback` funkce zpětného volání.  
  
 `context`  
 [in] Ukazatel na Win32 `CONTEXT` strukturou, který se používá k procházení zásobníku počáteční hodnoty. Win32 `CONTEXT` struktura obsahuje hodnoty registrů procesoru a představuje stav procesoru v určitém okamžiku v čase.  
  
 Počáteční hodnotu pomáhá určit, kde začít procházení zásobníku, pokud horní části zásobníku je kód pomocného objektu nespravovaného; CLR v opačném případě se ignoruje počáteční hodnotu. Základní hodnota musí být dodány pro asynchronní procházení. Pokud provádíte synchronní procházení, je nezbytné žádné počáteční hodnoty.  
  
 `context` Parametr je platný jenom v případě, že byla předána COR_PRF_SNAPSHOT_CONTEXT příznak `infoFlags` parametru.  
  
 `contextSize`  
 [in] Velikost `CONTEXT` strukturu, která odkazuje `context` parametru.  
  
## <a name="remarks"></a>Poznámky  
 Předání hodnotou null pro `thread` vrací snímek aktuální vlákno. Snímky lze pouze v případě, že cílové vlákno je pozastaveno v době pořizovat z jiných vláken.  
  
 Pokud profiler chce procházení zásobníku, volá `DoStackSnapshot`. Předtím, než se z tohoto volání vrátí hodnotu CLR, zavolá váš `StackSnapshotCallback` několikrát, jednou pro každé spravované rámce (nebo spuštění nespravované rámce) v zásobníku. Vyskytne nespravované snímků můžete musí si je sami.  
  
 Pořadí, ve kterém je šel zásobníku je opakem jak snímky byly vloženy do zásobníku: listové poslední (naposledy vloženo) rámce první, hlavní (první vloženo) rámce.  
  
 Další informace o tom, jak programovat profiler, aby procházel spravované zásobníky, viz [Profiler procházení zásobníku v rozhraní .NET Framework 2.0: Základy i mimo ně](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Procházení zásobníku může být synchronní nebo asynchronní, jak je popsáno v následujících částech.  
  
## <a name="synchronous-stack-walk"></a>Synchronní zásobníku  
 Procházení zásobníku synchronní zahrnuje procházení zásobníku aktuální vlákno v reakci na zpětné volání. Nevyžaduje se synchronizace replik indexů nebo pozastavení.  
  
 Provedení synchronního volání, když v reakci na volání jedné z váš profiler CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (nebo [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) volání metody, `DoStackSnapshot` k procházení zásobníku aktuální vlákno. To je užitečné, pokud chcete zjistit, jak zásobníku funguje na oznámení, jako [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Stačí zavolat `DoStackSnapshot` v rámci vaší `ICorProfilerCallback` předejte null v `context` a `thread` parametry.  
  
## <a name="asynchronous-stack-walk"></a>Asynchronní zásobníku  
 Procházení zásobníku asynchronní zahrnuje procházení zásobníku jiném vlákně, nebo procházení zásobníku aktuálního vlákna, nejsou v reakci na zpětné volání, ale můžete se zneužitím ukazatele na instrukci aktuální vlákno. Asynchronní procházení vyžaduje počáteční hodnoty, pokud je horní části zásobníku nespravovaný kód, který není součástí platformy pro vyvolání (PInvoke) nebo volání COM, ale kód pomocného objektu v prostředí CLR samotný. Například kód, který nemá just-in-time (JIT) kompilaci nebo uvolňování paměti kolekce je kód pomocného objektu.  
  
 Získáte základní hodnota tak, že přímo pozastavení cílové vlákno a procházení svůj zásobník sami, dokud nenajdete horní spravované rámce. Po cílové vlákno je pozastaveno, získáte aktuální kontext register cílovým vláknem. V dalším kroku určete, zda kontext registru odkazuje na nespravovaný kód voláním [icorprofilerinfo::getfunctionfromip –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) – vrátí-li `FunctionID` rovná nule, rámec je příkaz nespravovaného kódu. Nyní procházení zásobníku až do dosažení první spravovaný snímek a pak vypočítá kontextu počáteční hodnoty na základě kontextu registru pro tento rámec.  
  
 Volání `DoStackSnapshot` s počáteční kontext začít asynchronní zásobníku. Pokud nezadáte počáteční hodnoty, `DoStackSnapshot` může přeskočit spravované rámce v horní části zásobníku a v důsledku toho vám poskytne procházení zásobníku neúplné. Pokud zadáte základní hodnota, musí odkazovat na zkompilovaný pomocí kompilátoru JIT nebo Native Image Generator (Ngen.exe) – generovaného kódu; v opačném případě `DoStackSnapshot` vrátí kód chyby, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Asynchronní zásobníku může snadno způsobit zablokování nebo přistupovat k narušení, pokud budete postupovat podle následujících pokynů:  
  
-   Při přímo pozastavit vlákna, mějte na paměti, že pouze vlákno, které dosud nespustil spravovaný kód může pozastavit jiné vlákno.  
  
-   Vždycky blokovat vaší [icorprofilercallback::threaddestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) zpětné volání, dokud se nedokončí procházení zásobníku bylo vlákno.  
  
-   Při volání profileru do CLR funkci, která může spustit uvolňování paměti není držitelem zámku. To znamená, že není držitelem zámku Pokud vlastnící vláken činí volání, které spustí uvolnění.  
  
 K dispozici je také riziku zablokování při volání `DoStackSnapshot` z vlákna, které váš profiler byl vytvořen tak, aby vás provedou zásobníku vlákna samostatný cílový. První vlákno, které jste vytvořili přejde do určité `ICorProfilerInfo*` metod (včetně `DoStackSnapshot`), modul CLR provede inicializaci jednotlivých vláken, specifická pro modul CLR v daném vláknu. Pokud váš profiler byla pozastavena cílové vlákno, jehož zásobníku se snažíte procházení a vlastnit zámek potřebný k provedení této vlákno inicializace došlo k této cílové vlákno, dojde k zablokování. Abyste zabránili tomuto vzájemnému zablokování, provést počáteční volání do `DoStackSnapshot` z vašeho vlákna profiler vytvořeného procesem samostatné cílové vlákno, ale ne pozastavit nejprve cílové vlákno. Tento počáteční volání zajišťuje, vlákno inicializace dokončit bez zablokování. Pokud `DoStackSnapshot` je úspěšné a aspoň jeden snímek sestavy od této chvíle bude bezpečný pro toto vlákno profileru vytvořili pozastavit všechny cílové vlákno a volání `DoStackSnapshot` procesem zásobníku bylo cílové vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
