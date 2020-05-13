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
ms.openlocfilehash: fa3cbfee0359b8477f9efe88fe72837b86611bf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212799"
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
 pro Konstanta [CorDebugNGenPolicy –](cordebugngenpolicy-enumeration.md) , která určuje, jak aplikace načítá nativní bitové kopie při spuštění pod spravovaným ladicím programem.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je zásada nastavená na úspěšnou, vrátí metoda `S_OK` . Pokud `ePolicy` je mimo rozsah hodnot výčtu definovaných v [CorDebugNGenPolicy –](cordebugngenpolicy-enumeration.md), metoda vrátí `E_INVALIDARG` a volání metody nemá žádný vliv. Pokud nelze aktualizovat zásady generátoru nativních bitových kopií (Ngen. exe), metoda se vrátí `E_FAIL` .  
  
 `ICorDebugProcess5::EnableNGenPolicy`Metodu lze volat kdykoli během životnosti procesu. Zásada je platná pro všechny moduly, které jsou načtené po nastavení zásad.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
