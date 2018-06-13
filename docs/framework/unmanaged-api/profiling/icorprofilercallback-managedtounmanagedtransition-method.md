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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0735e4c59ba609ed87d61aca737c4f8a4dab757a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453483"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition – metoda
Upozorní profileru došlo k chybě přechod ze spravovaného kódu na nespravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která je volána.  
  
 `reason`  
 [v] Hodnota [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) výčtu, která určuje, zda přechodu nebo došlo k chybě z důvodu volání nespravovaného kódu ze spravovaného kódu, z důvodu zpětné z některého nespravované spravované funkci.  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `reason` je COR_PRF_TRANSITION_CALL, funkce ID je, že nespravované funkce, které se nikdy sestavili jsme pomocí kompilátoru za běhu. Nespravované funkce mají základní informace související s nimi, jako je například název a některá metadata. Pokud nespravované funkce byla zavolána s použitím implicitního platformy vyvolání (kódu PInvoke), modul runtime nemůže určit cílové volání a hodnotu `functionId` bude mít hodnotu null. Další informace o implicitní PInvoke najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [UnmanagedToManagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
