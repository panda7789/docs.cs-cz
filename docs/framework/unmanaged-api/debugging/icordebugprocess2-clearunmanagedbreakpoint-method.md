---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc34ab9c8dbfe10282f36a241a4e433debef7dd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
Odebere dříve nastavené zarážku na danou adresu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] A `CORDB_ADDRESS` hodnotu, která určuje, kdy byl nastaven zarážce adresu.  
  
## <a name="remarks"></a>Poznámky  
 Zadaný zarážek by byla dříve nastavena starší voláním [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 `ClearUnmanagedBreakpoint` Metodu lze volat, když proces laděné běží.  
  
 `ClearUnmanagedBreakpoint` Metoda vrací kód chyby, pokud je připojen ladicí program v režimu jen pro spravované nebo pokud neexistuje žádné zarážek na zadané adrese.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
