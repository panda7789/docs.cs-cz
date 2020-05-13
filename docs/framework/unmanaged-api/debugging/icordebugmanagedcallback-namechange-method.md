---
title: ICorDebugManagedCallback::NameChange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212669"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a>ICorDebugManagedCallback::NameChange – metoda
Oznamuje ladicímu programu, že došlo ke změně názvu domény aplikace nebo vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která buď změnila název, nebo obsahuje vlákno, které má změnu názvu.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, které má změnu názvu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
