---
title: ICorDebugManagedCallback::LoadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: cd4a16bc8b48f147ed03555b51eee5f42a445bc6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212696"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule – metoda
Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) byl úspěšně načten.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byl modul načten.  
  
 `pModule`  
 pro Ukazatel na objekt ICorDebugModule, který představuje modul CLR.  
  
## <a name="remarks"></a>Poznámky  
 `LoadModule`Zpětné volání poskytuje vhodný čas pro prověření metadat pro modul, nastavování příznaků kompilátoru JIT (just-in-time) nebo povolení nebo zakázání zpětného volání pro načítání tříd pro modul.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [UnloadModule – metoda](icordebugmanagedcallback-unloadmodule-method.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
