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
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781533"
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
 pro Hodnota výčtu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce  
  
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

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
