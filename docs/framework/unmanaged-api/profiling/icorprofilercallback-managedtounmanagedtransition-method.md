---
title: ICorProfilerCallback::ManagedToUnmanagedTransition – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 9b53030fe860e02b0afd0dce3055ac3cf29e3491
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499997"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition – metoda
Upozorní profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID volané funkce.  
  
 `reason`  
 pro Hodnota výčtu [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , která určuje, zda došlo k přechodu z důvodu volání do nespravovaného kódu ze spravovaného kódu nebo z důvodu návratu ze spravované funkce volané nespravovaným kódem.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `reason` je hodnota COR_PRF_TRANSITION_CALL, ID funkce je taková, že se jedná o nespravovanou funkci, která nebude nikdy zkompilována pomocí kompilátoru just-in-time. K nespravovaným funkcím jsou přidružené základní informace, jako je název a některá metadata. Pokud byla nespravovanou funkci volána pomocí implicitního vyvolání platformy (PInvoke), modul runtime nemůže určit cíl volání a hodnota `functionId` bude null. Další informace o implicitních PInvoke najdete v tématu [použití zprostředkovatele komunikace C++ (implicitní PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition – metoda](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [Použití explicitního PInvoke v jazyce C++ (atribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
