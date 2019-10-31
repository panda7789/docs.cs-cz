---
title: ICorDebugManagedCallback2::Exception – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: f40030a2034057e83de51a21655a686f30b9ee88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137445"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception – metoda
Oznamuje ladicímu programu, že bylo zahájeno hledání obslužné rutiny výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vyvolána.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, na kterém byla vyvolána výjimka.  
  
 `pFrame`  
 pro Ukazatel na objekt ICorDebugFrame, který představuje rámec určený parametrem `dwEventType`. Další informace najdete v tabulce v části poznámky.  
  
 `nOffset`  
 pro Celé číslo, které určuje posun, jak je určeno parametrem `dwEventType`. Další informace najdete v tabulce v části poznámky.  
  
 `dwEventType`  
 pro Hodnota výčtu CorDebugExceptionCallbackType –, která určuje typ zpětného volání výjimky.  
  
 `dwFlags`  
 pro Hodnota výčtu [CorDebugExceptionFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce  
  
## <a name="remarks"></a>Poznámky  
 `Exception` zpětné volání se volá v různých bodech ve fázi hledání v procesu zpracování výjimek. To znamená, že může být voláno více než jednou při odvíjení výjimky.  
  
 Zpracovávaná výjimka může být načtena z objektu ICorDebugThread, na který odkazuje parametr `pThread`.  
  
 Konkrétní rámec a posun jsou určeny parametrem `dwEventType` následujícím způsobem:  
  
|Hodnota `dwEventType`|Hodnota `pFrame`|Hodnota `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Rámec, který vyvolal výjimku.|Ukazatel na instrukci v rámci.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Rámec uživatelského kódu nejblíže k bodu vyvolané výjimky.|Ukazatel na instrukci v rámci.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Rámec obsahující popisovač catch.|Posun jazyka MSIL (Microsoft Intermediate Language) od začátku obslužné rutiny catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Nedefinované.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
