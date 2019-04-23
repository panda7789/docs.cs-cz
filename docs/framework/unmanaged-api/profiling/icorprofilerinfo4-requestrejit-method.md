---
title: ICorProfilerInfo4::RequestReJIT – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ddad2497f18aa510ade41f58ba20c9de1a46ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135093"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT – metoda
Požadavků opětovnou kompilaci JIT všechny výskyty zadaných funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Počet funkcí znovu zkompilovat.  
  
 `moduleIds`  
 [in] Určuje `moduleId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být překompilovány.  
  
 `methodIds`  
 [in] Určuje `methodId` část (`module`, `methodDef`) dvojice, které identifikují funkcí, které mají být překompilovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Byl proveden pokus o pro označení všech metod rekompilace JIT. Profiler musí implementovat [icorprofilercallback4::rejiterror –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodou ke zjištění, které metody byly úspěšně označen pro opětovnou kompilaci JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profiler musí implementovat [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní pro toto volání a proto není podporován.|  
|CORPROF_E_REJIT_NOT_ENABLED|Rekompilace JIT není povolená. Musíte povolit rekompilace JIT při inicializaci pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody nastavte `COR_PRF_ENABLE_REJIT` příznak.|  
|E_INVALIDARG|`cFunctions` je 0, nebo `moduleIds` nebo `methodIds` je `NULL`.|  
|||  
|E_OUTOFMEMORY|Modul CLR nemohl dokončit požadavek, protože mu došla paměť.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `RequestReJIT` má modul runtime znovu zkompilovat zadanou sadu funkcí. Profileru kód pak může použít [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní a upravte kód, který se vygeneruje, když funkce se překompilují. Toto nastavení neovlivní aktuálně prováděné funkce a volání pouze budoucí funkce. Pokud některý z určené funkce byl dříve překompilován JIT, požaduje Opětovná kompilace je ekvivalentní k vrácení zpět a znovu zkompiluje funkci. Pokud chcete zachovat vratnost, když kompilátor JIT kompilaci původní verzi funkce, považuje pouze původní verze jeho volané pro vkládání rozhodnutí. Když kompilátor JIT znovu zkompiluje funkci, považuje za aktuální verze (překompilovanou nebo původní) jeho volané pro vkládání.  
  
 Profiler volá obvykle `RequestReJIT` v reakci na vstup uživatele požaduje, aby profileru instrumentace jednu nebo více metod. `RequestReJIT` modul runtime, aby bylo možné provést některé své práce a může potenciálně aktivační události uvolňování paměti obvykle pozastaví. V důsledku toho by měly volat profiler `RequestReJIT` z vlákna se dřív vytvořili, a z CLR vytvoří vlákno, které aktuálně nezpracovává zpětného volání profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
