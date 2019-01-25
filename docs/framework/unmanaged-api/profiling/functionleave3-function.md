---
title: FunctionLeave3 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee72974d42842f63347c76586c4f1316f2a8f3a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683359"
---
# <a name="functionleave3-function"></a>FunctionLeave3 – funkce
Oznámí profileru, že se řízení vrací z funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionOrRemappedID`  
 [in] Identifikátor funkce, ve kterém ovládací prvek se vrátí.  
  
## <a name="remarks"></a>Poznámky  
 `FunctionLeave3` Funkce zpětného volání oznámí profileru jako funkce je volána, ale nepodporuje kontrolu návratovou hodnotu. Použití [icorprofilerinfo3::setenterleavefunctionhooks3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) k registraci vaši implementaci této funkce.  
  
 `FunctionLeave3` Funkce je zpětné volání, je nutné implementovat. Musíte použít implementaci `__declspec(naked)` atribut třídy úložiště.  
  
 Prováděcí modul nelze uložit žádné registry před voláním této funkce.  
  
-   Při vstupu je nutné uložit všechny registrů, které používáte, včetně těch v jednotku s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku pomocí automaticky otevíraného vypnout všechny parametry, které byly nahrány jeho volajícím.  
  
 Provádění `FunctionLeave3` by neměla blokovat, protože způsobí zpoždění uvolnění paměti. Implementace by se neměly pokoušet uvolnění paměti, protože zásobníku nemusí být ve stavu přívětivá kolekce uvolnění paměti. Při pokusu o uvolnění modulu runtime bude blokovat až do `FunctionLeave3` vrátí.  
  
 `FunctionLeave3` Funkce nesmí volat do spravovaného kódu nebo způsobit přidělování spravované paměti žádným způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
