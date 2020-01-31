---
title: ICorDebugManagedCallback2::ExceptionUnwind – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788280"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind – metoda
Poskytuje oznámení o stavu během procesu odvíjení výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vyvolána.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, na kterém byla vyvolána výjimka.  
  
 `dwEventType`  
 pro Hodnota výčtu CorDebugExceptionUnwindCallbackType –, která určuje událost, která je signálem zpětného volání během fáze unwind.  
  
 `dwFlags`  
 pro Hodnota výčtu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce.  
  
## <a name="remarks"></a>Poznámky  
 `ExceptionUnwind` je volána v různých bodech během fáze unwind v procesu zpracování výjimek. `ExceptionUnwind` lze volat více než jednou při odvíjení jedné výjimky.  
  
 Pokud `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, bude ukazatel na instrukci v rámci koncového bodu vlákna před (to může být několik pokynů před) instrukcí, která vedla k výjimce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
