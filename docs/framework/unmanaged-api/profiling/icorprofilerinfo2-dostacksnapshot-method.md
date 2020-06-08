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
ms.openlocfilehash: b9a7142de01d818390b740a795f70a4606952780
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497371"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot – metoda
Projde spravované snímky v zásobníku pro zadané vlákno a pošle informace do profileru prostřednictvím zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro ID cílového vlákna  
  
 Předání hodnoty null v rámci `thread` vypočítá snímek aktuálního vlákna. Pokud `ThreadID` je předán jiný podproces, modul CLR (Common Language Runtime) pozastaví toto vlákno, provede snímek a obnoví.  
  
 `callback`  
 pro Ukazatel na implementaci metody [StackSnapshotCallback –](stacksnapshotcallback-function.md) , která je volána modulem CLR k poskytnutí informací o každém spravovaném snímku a každém spuštění nespravovaných snímků.  
  
 `StackSnapshotCallback`Metoda je implementována modulem pro zápis profileru.  
  
 `infoFlags`  
 pro Hodnota výčtu [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) , která určuje množství dat, která se mají zpětně předat pro každý rámec `StackSnapshotCallback` .  
  
 `clientData`  
 pro Ukazatel na data klienta, která jsou předána přímo do `StackSnapshotCallback` funkce zpětného volání.  
  
 `context`  
 pro Ukazatel na `CONTEXT` strukturu Win32, která se používá k osazení procházení zásobníku. Struktura Win32 `CONTEXT` obsahuje hodnoty registrů CPU a představuje stav procesoru v určitém okamžiku v čase.  
  
 Tato semena pomáhá modulu CLR určit, kde začít procházet zásobníkem, pokud je horní část zásobníku nespravovaným kódem pomocníka; v opačném případě se počáteční hodnoty ignorují. Pro asynchronní procházení je nutné zadat počáteční hodnotu. Pokud provádíte synchronní procházení, není nutné žádné osivo.  
  
 `context`Parametr je platný pouze v případě, že byl do parametru předán příznak COR_PRF_SNAPSHOT_CONTEXT `infoFlags` .  
  
 `contextSize`  
 pro Velikost `CONTEXT` struktury, na kterou se odkazuje `context` parametr.  
  
## <a name="remarks"></a>Poznámky  
 Předání hodnoty null pro `thread` vypočítá snímek aktuálního vlákna. Snímky lze považovat z jiných vláken pouze v případě, že cílové vlákno je pozastaveno v čase.  
  
 Když profiler chce projít zásobníkem, volá `DoStackSnapshot` . Před tím, než se CLR vrátí z tohoto volání, zavolá `StackSnapshotCallback` několikrát, jednou pro každý spravovaný rámec (nebo spuštění nespravovaných snímků) v zásobníku. V případě, že dojde k nespravovaným snímkům, musíte si je projít sami.  
  
 Pořadí, ve kterém je zásobník vás provedl, je opakem způsobu, jakým byly snímky vloženy do zásobníku: první snímek (naposledy vloženo), hlavní snímek (první snímek), který byl naposledy posunut.  
  
 Další informace o tom, jak profiler naprogramovat k procházení spravovaných zásobníků, najdete v tématu prochází [se v zásobníku profileru v .NET Framework 2,0: základy a více](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).  
  
 Procházení zásobníku může být synchronní nebo asynchronní, jak je vysvětleno v následujících částech.  
  
## <a name="synchronous-stack-walk"></a>Synchronní procházení zásobníku  
 Synchronní procházení zásobníku zahrnuje procházení zásobníku aktuálního vlákna v reakci na zpětné volání. Nevyžaduje osazení ani pozastavení.  
  
 Provádíte synchronní volání, když v reakci na rozhraní CLR volání jedné z metod [ICorProfilerCallback](icorprofilercallback-interface.md) (nebo [ICorProfilerCallback2](icorprofilercallback2-interface.md)) vašeho profileru zavoláte, abyste provedli `DoStackSnapshot` průchod zásobníku aktuálního vlákna. To je užitečné v případě, že chcete zjistit, jak má zásobník vypadat v oznámení, jako je například [ICorProfilerCallback:: ObjectAllocated –](icorprofilercallback-objectallocated-method.md). Stačí zavolat `DoStackSnapshot` z vaší metody a `ICorProfilerCallback` předat hodnotu null v `context` `thread` parametrech a.  
  
## <a name="asynchronous-stack-walk"></a>Asynchronní procházení zásobníku  
 Asynchronní procházení zásobníku má za následek procházení zásobníku různých vláken nebo procházení zásobníku aktuálního vlákna, nikoli v reakci na zpětné volání, ale napadení ukazatele na instrukci aktuálního vlákna. Asynchronní procházení vyžaduje počáteční hodnotu, pokud je horní část zásobníku nespravovaný kód, který není součástí vyvolání platformy (PInvoke) nebo volání rozhraní COM, ale pomocný kód v samotném modulu CLR. Například kód, který provádí kompilaci JIT (just-in-time) nebo uvolňování paměti, je kód pomocníka.  
  
 Můžete získat počáteční hodnotu přímo pozastavením cílového vlákna a procházením jeho zásobníku, dokud nenajdete nejvyšší spravovaný rámec. Po pozastavení cílového vlákna získá aktuální kontext registru cílového vlákna. Dále určete, zda kontext registrace odkazuje na nespravovaný kód voláním [ICorProfilerInfo:: GetFunctionFromIP –](icorprofilerinfo-getfunctionfromip-method.md) – Pokud vrátí hodnotu `FunctionID` nula, je rámec nespravovaným kódem. Nyní sejděte do zásobníku, dokud nedosáhnete prvního spravovaného rámce, a pak Vypočtěte počáteční kontext na základě kontextu registru pro tento rámec.  
  
 Voláním `DoStackSnapshot` kontextu počátečního rozhraní zahajte procházení asynchronního zásobníku. Pokud nezadáte osazení, může se stát, že se `DoStackSnapshot` v horní části zásobníku přeskočí spravované snímky, a v důsledku toho vám poskytne nekompletní procházení zásobníku. Pokud zadáte počáteční hodnotu, musí odkazovat na generátor JIT nebo nativní bitové kopie (Ngen. exe) generovaný kódem; v opačném případě `DoStackSnapshot` vrátí kód chyby CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Asynchronní procházení zásobníku může snadno způsobit zablokování nebo porušení přístupu, pokud nedodržujete tyto pokyny:  
  
- Při přímém pozastavení vláken mějte na paměti, že pouze vlákno, které nikdy nespouštělo spravovaný kód, může pozastavit jiné vlákno.  
  
- Vždy zablokovat volání [ICorProfilerCallback:: ThreadDestroyed –](icorprofilercallback-threaddestroyed-method.md) , dokud není dokončeno procházení zásobníku tohoto vlákna.  
  
- Nedržte zámek, dokud profiler zavolá funkci CLR, která může aktivovat uvolňování paměti. To znamená, že nedržíte zámek, pokud vlastnící vlákno může učinit volání, které vyvolá uvolňování paměti.  
  
 Existuje také riziko zablokování při volání `DoStackSnapshot` z vlákna, které vytvořil Profiler, abyste mohli procházet zásobník samostatného cílového vlákna. Při prvním vložení vlákna, které jste vytvořili, zadá určité `ICorProfilerInfo*` metody (včetně `DoStackSnapshot` ), CLR provede v tomto vláknu inicializaci specifickou pro vlákno, CLR. Pokud váš Profiler pozastavil cílové vlákno, u kterého se pokoušíte Procházet, a v případě, že se u tohoto cílového vlákna stala vlastní zámek potřebný k provedení této inicializace pro vlákno, dojde k zablokování. Chcete-li se tomuto zablokování vyhnout, proveďte počáteční volání `DoStackSnapshot` z vlákna vytvořeného profilerem a Projděte si samostatné cílové vlákno, ale Neblokujte nejprve cílové vlákno. Toto počáteční volání zajistí, že inicializace jednotlivých vláken může být dokončena bez zablokování. Pokud `DoStackSnapshot` uspěje a sestaví alespoň jeden rámec, bude po tomto okamžiku bezpečný pro toto vlákno vytvořené profilerem, aby se pozastavilo jakékoli cílové vlákno, a zavolá se `DoStackSnapshot` do zásobníku daného cílového vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
