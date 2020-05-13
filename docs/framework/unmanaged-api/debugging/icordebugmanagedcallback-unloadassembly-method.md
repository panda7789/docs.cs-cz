---
title: ICorDebugManagedCallback::UnloadAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 07996a78d7f559de587c8a3eb2babfc06675169d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212643"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a>ICorDebugManagedCallback::UnloadAssembly – metoda
Oznamuje ladicímu programu, že bylo uvolněno sestavení společného jazykového modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje aplikační doménu, která obsahuje sestavení.  
  
 `pAssembly`  
 pro Ukazatel na objekt ICorDebugAssembly, který představuje sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Po tomto zpětném volání by se nemělo používat sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [LoadAssembly – metoda](icordebugmanagedcallback-loadassembly-method.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
