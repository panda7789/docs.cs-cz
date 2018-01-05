---
title: "ICorDebugManagedCallback2::Exception – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception – metoda
Aby bylo zahájeno hledání pro obslužnou rutinu výjimky upozorní ladicího programu.  
  
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
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující vláken, na kterém byla výjimka vydána.  
  
 `pThread`  
 [v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byla výjimka vydána.  
  
 `pFrame`  
 [v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, počítáno od `dwEventType` parametr. Další informace najdete v tabulce v oddílu Poznámky.  
  
 `nOffset`  
 [v] Celé číslo, které určuje posun, počítáno od `dwEventType` parametr. Další informace najdete v tabulce v oddílu Poznámky.  
  
 `dwEventType`  
 [v] Hodnota CorDebugExceptionCallbackType – výčet, který určuje typ této výjimky zpětného volání.  
  
 `dwFlags`  
 [v] Hodnota [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) výčet, který určuje další informace o výjimce  
  
## <a name="remarks"></a>Poznámky  
 `Exception` Zpětné volání je volána v různých okamžicích v průběhu vyhledávání fáze procesu zpracování výjimek. To znamená, že ho lze volat více než jednou při unwinding výjimku.  
  
 Výjimka zpracovává mohou být načteny z objektu ICorDebugThread odkazuje `pThread` parametr.  
  
 Určitého snímku a posun jsou určeny `dwEventType` parametr následujícím způsobem:  
  
|Hodnota`dwEventType`|Hodnota`pFrame`|Hodnota`nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Rámečku, která vrátila výjimku.|Ukazatel instrukce v rámečku.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Na uživatelském kódu rámce nejbližší bod vyvolaná výjimka.|Ukazatel instrukce v rámečku.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Rámce, který obsahuje obslužná rutina catch.|Posun Microsoft (MSIL intermediate language) na začátek obslužná rutina catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Není definována.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
