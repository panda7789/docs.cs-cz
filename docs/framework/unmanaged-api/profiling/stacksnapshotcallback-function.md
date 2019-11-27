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
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427076"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback – funkce
Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 pro Pokud je tato hodnota nula, toto zpětné volání slouží pro spuštění nespravovaných snímků. v opačném případě je to identifikátor spravované funkce a toto zpětné volání je pro spravovaný rámec.  
  
 `ip`  
 pro Hodnota ukazatele na instrukci nativního kódu v rámci.  
  
 `frameInfo`  
 pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku. Tato hodnota je platná pro použití pouze během tohoto zpětného volání.  
  
 `contextSize`  
 pro Velikost `CONTEXT` struktury, na kterou se odkazuje parametr `context`  
  
 `context`  
 pro Ukazatel na strukturu `CONTEXT` Win32, která představuje stav procesoru pro tento rámec.  
  
 Parametr `context` je platný pouze v případě, že byl předán příznak COR_PRF_SNAPSHOT_CONTEXT v `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 pro Ukazatel na data klienta, která jsou předána přímo z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `StackSnapshotCallback` je implementovaná modulem pro zápis profileru. Je nutné omezit složitost práce v `StackSnapshotCallback`. Například při použití `ICorProfilerInfo2::DoStackSnapshot` asynchronním způsobem může cílové vlákno držet zámky. Pokud kód v `StackSnapshotCallback` vyžaduje stejné zámky, může zablokování následovat.  
  
 Metoda `ICorProfilerInfo2::DoStackSnapshot` volá funkci `StackSnapshotCallback` jednou pro spravovaný rámec nebo jednou za spuštění nespravovaných snímků. Pokud je zavolána `StackSnapshotCallback` pro spuštění nespravovaných snímků, profiler může použít kontext registrace (odkazovaná parametrem `context`) k provedení vlastního nespravovaného zásobníku. V tomto případě struktura `CONTEXT` Win32 představuje stav procesoru pro poslední vloženou snímek v rámci spuštění nespravovaných snímků. I když struktura `CONTEXT` Win32 zahrnuje hodnoty pro všechny Registry, měli byste spoléhat jenom na hodnoty registru ukazatelů zásobníku, registru ukazatelů na rámec, registru ukazatele na instrukce a na nestálé (tj. zachované) celočíselné registry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
