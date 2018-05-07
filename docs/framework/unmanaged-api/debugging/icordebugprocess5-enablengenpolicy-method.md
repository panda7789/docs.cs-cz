---
title: ICorDebugProcess5::EnableNGENPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c598491acd27223a8a41234ddf2c6b8e6f005d52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy – metoda
Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ePolicy`  
 [v] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) konstanta, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zásada nastavená úspěšně, vrátí metoda `S_OK`. Pokud `ePolicy` je mimo rozsah výčtové hodnoty definované [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), vrátí metoda `E_INVALIDARG` a volání metody, které nemá žádný vliv. Pokud nelze aktualizovat zásady generátor (Ngen.exe), vrátí metoda `E_FAIL`.  
  
 `ICorDebugProcess5::EnableNGenPolicy` Nelze volat metodu v průběhu životního cyklu procesu. Pro všechny moduly, které jsou načteny po nastavení zásad platí zásady.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
