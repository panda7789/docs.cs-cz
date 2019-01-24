---
title: StackSnapshotCallback – funkce
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e73afa7ef33e12d6bc658c944c79ce1bc4f94f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572412"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback – funkce
Poskytuje informace o každý spravovaný rámec a každé spuštění nespravované rámce v zásobníku během procházení zásobníku, která inicializuje profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Pokud tato hodnota je nula, je tato zpětné volání pro spuštění nespravované snímky. v opačném případě je to identifikátor spravované funkce a je tato zpětné volání pro spravovaný rámec.  
  
 `ip`  
 [in] Hodnota ukazatele na instrukci nativního kódu v rámci.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o zásobníku. Tato hodnota je platná pro použití pouze během tohoto zpětného volání.  
  
 `contextSize`  
 [in] Velikost `CONTEXT` strukturu, která odkazuje `context` parametru.  
  
 `context`  
 [in] Ukazatel na Win32 `CONTEXT` struktura, která představuje stav procesoru pro tento rámec.  
  
 `context` Parametr je platný jenom v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Ukazatel na data klienta, který se předává přímo z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Poznámky  
 `StackSnapshotCallback` Funkce je implementováno tvůrci profileru. Je třeba omezit složitost práci v `StackSnapshotCallback`. Například při použití `ICorProfilerInfo2::DoStackSnapshot` v asynchronním režimu cílové vlákno může být zámky. Pokud kódu v rámci `StackSnapshotCallback` vyžaduje stejné uzamčení, zablokování může následovat.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Volání metod `StackSnapshotCallback` funkce jednou pro každý spravovaný snímek nebo jednou za běhu nespravované snímků. Pokud `StackSnapshotCallback` je volána pro spuštění nespravované snímků, profiler může použít kontext registr (odkazuje `context` parametr) provádět vlastní nespravovaná zásobníku. V takovém případě Win32 `CONTEXT` struktura představuje stav procesoru pro nedávno vložené rámce v rámci běhu nespravované snímků. I když Win32 `CONTEXT` struktura obsahuje hodnoty pro všechny registrů, by se neměla spoléhat jenom na hodnoty registru ukazatel zásobníku, registr ukazatelů rámce, registr ukazatele instrukcí a stálé (který se zachovají) celočíselné registry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
