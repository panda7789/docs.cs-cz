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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d46dcd43ffe6963d1177a395b855a287182cdff0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685630"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception – metoda
Upozorní ladicího programu, že bylo zahájeno hledání pro obslužnou rutinu výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, na kterém byla výjimka vydána.  
  
 `pThread`  
 [in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla výjimka vydána.  
  
 `pFrame`  
 [in] Ukazatel na objekt ICorDebugFrame, který představuje rámec, počítáno od `dwEventType` parametru. Další informace najdete v tabulce v oddílu Poznámky.  
  
 `nOffset`  
 [in] Celé číslo, které určuje prodlevu, počítáno od `dwEventType` parametru. Další informace najdete v tabulce v oddílu Poznámky.  
  
 `dwEventType`  
 [in] Hodnota cordebugexceptioncallbacktype – výčet, který určuje typ této výjimky zpětného volání.  
  
 `dwFlags`  
 [in] Hodnota [cordebugexceptionflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce  
  
## <a name="remarks"></a>Poznámky  
 `Exception` Zpětného volání je volána v různých fázích v průběhu fáze hledání procesu zpracování výjimek. To znamená ho může být volána více než jednou při uvolnění výjimku.  
  
 Zpracovává výjimky můžete získat z objekt ICorDebugThread, na který odkazuje `pThread` parametru.  
  
 Konkrétní rámce a posun jsou určeny `dwEventType` parametr následujícím způsobem:  
  
|Hodnota `dwEventType`|Hodnota `pFrame`|Hodnota `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Rámce, který vyvolal výjimku.|Ukazatele na instrukci v rámci.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Snímek uživatelského kódu co nejblíž koncovým bodem vyvolané výjimky.|Ukazatele na instrukci v rámci.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Rámce, který obsahuje obslužné rutiny catch.|Posun Microsoft intermediate language (MSIL) od obslužné rutiny catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Nedefinovaný.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
