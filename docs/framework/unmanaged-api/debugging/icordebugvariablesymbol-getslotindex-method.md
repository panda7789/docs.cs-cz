---
title: 'ICorDebugVariableSymbol:: GetSlotIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790896"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol:: GetSlotIndex – metoda
Načte index spravovaného slotu místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 mimo Ukazatel na index slotu místní proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud bylo úspěšné. `E_FAIL`, je-li proměnná argumentem funkce.  
  
## <a name="remarks"></a>Poznámky  
 K načtení informací o metadatech proměnné lze použít index spravované patice místní proměnné.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableSymbol – rozhraní](icordebugvariablesymbol-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
