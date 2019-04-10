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
ms.openlocfilehash: 154243e45a41ec2ba8b02937794b372a0705d458
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219119"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy – metoda
Nastaví hodnotu, která určuje, jak aplikace načítá nativních bitových kopií při spuštění v rámci spravovaného ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ePolicy`  
 [in] A [cordebugngenpolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) konstantu, která určuje, jak aplikace načítá nativních bitových kopií při spuštění v rámci spravovaného ladicího programu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zásada nastavená úspěšně, metoda vrátí `S_OK`. Pokud `ePolicy` je mimo rozsah výčtové hodnoty určené [cordebugngenpolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), vrátí metoda `E_INVALIDARG` a volání metody, které nemá žádný vliv. Pokud nelze aktualizovat zásady Native Image Generator (Ngen.exe), metoda vrátí `E_FAIL`.  
  
 `ICorDebugProcess5::EnableNGenPolicy` Metodu lze volat kdykoli po celou dobu životnosti procesu. Zásady platí pro všechny moduly, které jsou načteny po nastavení zásad.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
