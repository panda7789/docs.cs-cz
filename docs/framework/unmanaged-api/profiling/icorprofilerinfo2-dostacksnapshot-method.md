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
ms.openlocfilehash: 338120932b0bcbe390332515856aaeaa3bc34a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot – metoda
Provede spravované rámce v zásobníku pro zadaný vlákno a odesílá informace do profileru prostřednictvím zpětné volání.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `thread`  
 [v] ID cílového vlákno.  
  
 Předání hodnotou null v `thread` vypočítá snímek aktuální vlákno. Pokud `ThreadID` z jiné vlákno je předán, modul CLR (CLR) pozastaví daném vláknu, provede snímku a obnoví.  
  
 `callback`  
 [v] Ukazatel na implementaci [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) metodu, která je volána metodou CLR profileru poskytnout informace o každé spravované rámečkem a každé spuštění nespravované rámce.  
  
 `StackSnapshotCallback` Je implementována metoda modul pro zápis profileru.  
  
 `infoFlags`  
 [v] Hodnota [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) výčtu, který určuje množství dat, které mají být předány zpět pro každý snímek pomocí `StackSnapshotCallback`.  
  
 `clientData`  
 [v] Ukazatel na klienta data, která je předána přímo do `StackSnapshotCallback` funkce zpětného volání.  
  
 `context`  
 [v] Ukazatel na Win32 `CONTEXT` strukturu, která se používá k procházení zásobníku počáteční hodnoty. Win32 `CONTEXT` struktura obsahuje hodnoty registrů procesoru a představuje stav procesoru v určitém okamžiku v čase.  
  
 Počáteční hodnoty pomáhá určit, kde začít procházení zásobníku, pokud je horní části zásobníku kód pomocného objektu nespravované; modulu CLR počáteční hodnoty, jinak hodnota se ignoruje. Je nutné zadat počáteční hodnoty pro asynchronní procházení. Pokud byste synchronní procházení, je nutné žádné počáteční hodnoty.  
  
 `context` Parametr je platný pouze v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `infoFlags` parametr.  
  
 `contextSize`  
 [v] Velikost `CONTEXT` strukturu, která odkazuje `context` parametr.  
  
## <a name="remarks"></a>Poznámky  
 Předání hodnotou null pro `thread` vypočítá snímek aktuální vlákno. Snímky lze pořizovat další podprocesy pouze v případě, že cíl vlákno je pozastaveno v době.  
  
 Profileru chce provede zásobníku, volá `DoStackSnapshot`. Před modulu CLR vrátí z tohoto volání, zavolá váš `StackSnapshotCallback` několikrát, jednou pro každý spravovaný rámce (nebo spuštění nespravované rámce) v zásobníku. Pokud nedojde k nespravované rámce, můžete musí provede je sami.  
  
 Pořadí, ve kterém je proveden vaši firmu zásobníku je opakem jak snímky byly vloženy do zásobníku: poslední list (poslední nabídnutých) snímek první, hlavní (první nabídnutých) snímku.  
  
 Další informace o tom, jak program profileru vás spravované zásobníky najdete v tématu [profileru zásobníku proti v rozhraní .NET Framework 2.0: základy a kromě](http://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Procházení zásobníku může být synchronní nebo asynchronní, jak je popsáno v následujících částech.  
  
## <a name="synchronous-stack-walk"></a>Procházení synchronní zásobníku  
 Procházení zásobníku synchronní zahrnuje proti zásobník aktuálního vlákna v reakci na zpětné volání. Nevyžaduje se synchronizace replik indexů nebo přechodem do režimu spánku.  
  
 Provedete synchronní, při volání v reakci na CLR volání jedné z vaší profileru [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (nebo [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) volání metody, `DoStackSnapshot` vás zásobník aktuální vlákno. To je užitečné, když chcete zobrazit, co se zásobníkem vypadá na oznámení, jako [icorprofilercallback::objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Stačí zavolat `DoStackSnapshot` uvnitř vaší `ICorProfilerCallback` metodu a předá hodnotu null v `context` a `thread` parametry.  
  
## <a name="asynchronous-stack-walk"></a>Procházení asynchronní zásobníku  
 Procházení zásobníku asynchronní zahrnuje procházení zásobníku jiné vlákno nebo procházení zásobníku aktuální vlákno, není v odpovědi na zpětné volání, ale podle weby ukazatel instrukce aktuální vlákno. Asynchronní procházení vyžaduje počáteční hodnoty, pokud je horní části zásobníku nespravovaného kódu, který není součástí platformy vyvolání (kódu PInvoke) nebo volání COM, ale kód pomocného objektu CLR sám sebe. Kód, který nemá kolekci kompilování nebo paměti za běhu (JIT) je například kód pomocného objektu.  
  
 Získáte počáteční hodnoty tak, že přímo pozastavení vláken cíl a proti jeho zásobníku sami, vyhledejte nejhornější spravovat rámce. Po cíl vlákno je pozastaveno, získáte aktuální kontext registrace vlákno cíl. Dále určit, zda kontext registrace odkazuje na nespravovaný kód voláním [icorprofilerinfo::getfunctionfromip –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) – vrátí-li `FunctionID` rovná nule, je rámečku nespravovaného kódu. Nyní provede v zásobníku, dokud nepřejdete na první spravované rámce, pak vypočítat kontext počáteční hodnoty na základě kontextu registrace pro tento snímek.  
  
 Volání `DoStackSnapshot` s váš kontext počáteční hodnoty zahájíte procházení asynchronní zásobníku. Pokud nezadáte počáteční hodnoty, `DoStackSnapshot` může přeskočit spravované rámce v horní části zásobníku a proto vám poskytne procházení zásobníku neúplné. Pokud zadáte počáteční hodnoty, musí odkazovat na kompilována nebo Native Image Generator (Ngen.exe)-generovaného kódu; v opačném `DoStackSnapshot` vrátí kód chyby CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Asynchronní procházení zásobníku můžete snadno způsobit zablokování nebo přistupovat k narušení, pokud jste postupovali podle těchto pokynů:  
  
-   Po pozastavení přímo vláken, mějte na paměti, že pouze vlákno, které má nebude nikdy spuštěn spravovaného kódu můžete pozastavit jiné vlákno.  
  
-   Vždy blok ve vaší [icorprofilercallback::threaddestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) zpětného volání až do dokončení daném vláknu procházení zásobníku.  
  
-   Podržte zámek není, pokud vaše profileru zavolá funkci CLR, které můžete aktivovat uvolňování paměti. To znamená není držitelem zámek Pokud vlastnícím vlákno může provádět volání, která aktivuje uvolnění paměti.  
  
 K dispozici je také riziko vzájemného zablokování při volání `DoStackSnapshot` z vlákno, které vaše profileru vytvořil, aby můžete projde zásobník samostatný cílový vlákna. První vlákno, které jste vytvořili vstupuje do určité `ICorProfilerInfo*` metody (včetně `DoStackSnapshot`), modul CLR provede inicializaci specifické pro CLR v daném vláknu podle vláken. Pokud vaše profileru pozastavilo vlákno cíl jejichž zásobníku se pokoušíte provede, a pokud daném vláknu cíl se stalo s vlastní zámek potřebné k provedení této inicializace vlákno, dojde k zablokování. Abyste předešli této zablokování, provést počáteční volání do `DoStackSnapshot` z vaší profileru vytvořit vlákno vás samostatné cíle přístup z více vláken, ale není pozastavit nejprve vlákno cíl. Tento počáteční volání zajišťuje, zda inicializace vlákno dokončí bez vzájemného zablokování. Pokud `DoStackSnapshot` úspěšné a alespoň jeden snímek sestavy po tomto okamžiku je bezpečné pro přístup z tohoto profileru vytvořit vlákno pozastavit všechny cílové přístup z více vláken a volání `DoStackSnapshot` projde zásobník daném vláknu cíl.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
