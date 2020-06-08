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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493978"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback – funkce
Poskytuje Profiler s informacemi o každém spravovaném snímku a každém spuštění nespravovaných snímků v zásobníku během průchodu zásobníku, který je iniciován metodou [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
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
 pro `COR_PRF_FRAME_INFO`Hodnota, která odkazuje na informace o snímku zásobníku. Tato hodnota je platná pro použití pouze během tohoto zpětného volání.  
  
 `contextSize`  
 pro Velikost `CONTEXT` struktury, na kterou se odkazuje `context` parametr.  
  
 `context`  
 pro Ukazatel na `CONTEXT` strukturu Win32, která představuje stav procesoru pro tento rámec.  
  
 `context`Parametr je platný pouze v případě, že byl předán příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot` .  
  
 `clientData`  
 pro Ukazatel na data klienta, která jsou předána přímo do z `ICorProfilerInfo2::DoStackSnapshot` .  
  
## <a name="remarks"></a>Poznámky  
 `StackSnapshotCallback`Funkce je implementována modulem pro zápis profileru. Je nutné omezit složitost práce, která byla dokončena v `StackSnapshotCallback` . Například při použití `ICorProfilerInfo2::DoStackSnapshot` asynchronním způsobem může cílové vlákno držet zámky. Pokud kód v rámci `StackSnapshotCallback` vyžaduje stejné zámky, může zablokování následovat.  
  
 `ICorProfilerInfo2::DoStackSnapshot`Metoda volá `StackSnapshotCallback` funkci jednou pro každý spravovaný rámec nebo jednou za spuštění nespravovaných snímků. Pokud `StackSnapshotCallback` je volána pro spuštění nespravovaných snímků, profiler může použít kontext registrace (odkazovaná `context` parametrem) k provedení vlastního nespravovaného zásobníku. V tomto případě `CONTEXT` Struktura Win32 představuje stav procesoru pro poslední vloženou snímek v rámci spuštění nespravovaných snímků. I když `CONTEXT` Struktura Win32 zahrnuje hodnoty pro všechny Registry, měli byste spoléhat jenom na hodnoty registru ukazatelů zásobníku, registru ukazatelů na rozhraní, registru ukazatelů na instrukce a na nestálé (tj., zachované) celočíselné registry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
