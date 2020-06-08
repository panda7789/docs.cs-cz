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
ms.openlocfilehash: 8734fa9c9418b818cbe14ebe87ce2af6fa59c078
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499841"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition – metoda
Upozorní profileru, že došlo k přechodu z nespravovaného kódu do spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID volané funkce.  
  
 `reason`  
 pro Hodnota výčtu [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , která určuje, zda došlo k přechodu z důvodu volání spravovaného kódu z nespravovaného kódu nebo z důvodu návratu z nespravované funkce volané spravovaném rozhraním.  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `reason` je COR_PRF_TRANSITION_RETURN a není `functionId` null, je ID funkce nespravované funkce a nikdy nebude zkompilována pomocí kompilátoru JIT (just-in-time). Nespravované funkce mají přidružené základní informace, jako je název a některá metadata.  
  
 Pokud `reason` je hodnota COR_PRF_TRANSITION_CALL, může být možné, že volaná funkce (tj. spravovaná funkce) ještě nebyla kompilována JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition – metoda](icorprofilercallback-managedtounmanagedtransition-method.md)
- [Použití explicitního PInvoke v jazyce C++ (atribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Použití zprostředkovatele komunikace C++ (implicitní PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
