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
ms.openlocfilehash: 583819e8e7ab16a8ac1ce72892f4353e3043ce3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129687"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy – metoda
Nastaví hodnotu, která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ePolicy`  
 pro Konstanta [CorDebugNGenPolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) , která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zásada nastavená na úspěšnou, vrátí metoda `S_OK`. Pokud je `ePolicy` mimo rozsah hodnot výčtu definovaných hodnotou [CorDebugNGenPolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), metoda vrátí `E_INVALIDARG` a volání metody nemá žádný vliv. Pokud nelze aktualizovat zásady generátoru nativních bitových kopií (Ngen. exe), metoda vrátí `E_FAIL`.  
  
 Metodu `ICorDebugProcess5::EnableNGenPolicy` lze vyvolat kdykoli během doby platnosti procesu. Zásada je platná pro všechny moduly, které jsou načtené po nastavení zásad.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
