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
ms.openlocfilehash: 612b63ba9aa3504cab5196932293946d486955ce
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210199"
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
 pro Ukazatel na objekt ICorDebugFrame, který představuje rámec určený `dwEventType` parametrem. Další informace najdete v tabulce v části poznámky.  
  
 `nOffset`  
 pro Celé číslo, které určuje posun, jak je určeno `dwEventType` parametrem. Další informace najdete v tabulce v části poznámky.  
  
 `dwEventType`  
 pro Hodnota výčtu CorDebugExceptionCallbackType –, která určuje typ zpětného volání výjimky.  
  
 `dwFlags`  
 pro Hodnota výčtu [CorDebugExceptionFlags –](cordebugexceptionflags-enumeration.md) , která určuje další informace o výjimce  
  
## <a name="remarks"></a>Poznámky  
 `Exception`Zpětné volání je voláno v různých bodech ve fázi hledání v procesu zpracování výjimek. To znamená, že může být voláno více než jednou při odvíjení výjimky.  
  
 Zpracovávaná výjimka může být načtena z objektu ICorDebugThread, na který odkazuje `pThread` parametr.  
  
 Konkrétní rámec a posun jsou určeny následujícím `dwEventType` parametrem:  
  
|Hodnota`dwEventType`|Hodnota`pFrame`|Hodnota`nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Rámec, který vyvolal výjimku.|Ukazatel na instrukci v rámci.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Rámec uživatelského kódu nejblíže k bodu vyvolané výjimky.|Ukazatel na instrukci v rámci.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Rámec obsahující popisovač catch.|Posun jazyka MSIL (Microsoft Intermediate Language) od začátku obslužné rutiny catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Nedefinované.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
