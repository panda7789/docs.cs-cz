---
title: 'ICorDebugVariableSymbol:: GetSlotIndex – metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 251a978e96ff396d0d9d9282ded7f8a25ae0ba0b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397085"
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
 `S_OK`v případě úspěchu. `E_FAIL`je-li proměnná argumentem funkce.  
  
## <a name="remarks"></a>Poznámky  
 K načtení informací o metadatech proměnné lze použít index spravované patice místní proměnné.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugVariableSymbol – rozhraní](icordebugvariablesymbol-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
