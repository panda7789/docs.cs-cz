---
title: ICorDebug::SetManagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcf97f9fffabb9ae9579016517cfc335e6f783a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler – metoda
Určuje objekt obslužné rutiny události pro spravované události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [v] Ukazatel na [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objekt, který je objekt obslužné rutiny událostí.  
  
## <a name="remarks"></a>Poznámky  
 `SetManagedHandler` musí být voláno v okamžiku vytvoření.  
  
 Pokud `ICorDebugManagedCallback` implementace neobsahuje dostatek rozhraní pro zpracování události ladění pro aplikace, která je probíhá ladění, `SetManagedHandler` vrátí HRESULT E_NOINTERFACE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
