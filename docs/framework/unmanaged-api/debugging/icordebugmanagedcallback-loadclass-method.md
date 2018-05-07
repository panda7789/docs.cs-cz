---
title: ICorDebugManagedCallback::LoadClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1d920a97338bba3e90ec8f0c440f6dd2a93e722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass – metoda
Načtení třídy upozorní ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého se načetl třídy.  
  
 `c`  
 [v] Ukazatel na ICorDebugClass objekt, který představuje třídu.  
  
## <a name="remarks"></a>Poznámky  
 Tato zpětného volání dojde pouze v případě, že třída načítání je povoleno modul, který obsahuje třídu. Načtení třídy je vždy povolena pro dynamické moduly.  
  
 `LoadClass` Zpětné volání poskytuje příslušnou dobu pro vazbu na nově vygenerované třídy v dynamických modulech zarážky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [UnloadClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
