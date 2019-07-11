---
title: ICorProfilerCallback::UnmanagedToManagedTransition – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fa7dfe101b07ae6eb8d58daad85954f0ce29b02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747053"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition – metoda
Oznámí profileru, že došlo k přechodu z nespravovaného kódu pro spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, která je volána.  
  
 `reason`  
 [in] Hodnota [cor_prf_transition_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) výčet, který označuje, zda došlo k přechodu z důvodu volání do spravovaného kódu z nespravovaného kódu nebo z důvodu návrat z nespravované funkce volá spravovaný ten.  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `reason` je COR_PRF_TRANSITION_RETURN a `functionId` není null, funkce ID je, že z nespravované funkce a se nikdy již byly zkompilovány pomocí kompilátoru just-in-time (JIT). Nespravované funkce mají některé základní informace související s nimi, jako jsou název a některá metadata.  
  
 Pokud hodnota `reason` COR_PRF_TRANSITION_CALL, je to možné, že volaná funkce (to znamená, spravované funkce) ještě nebyla kompilována JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
