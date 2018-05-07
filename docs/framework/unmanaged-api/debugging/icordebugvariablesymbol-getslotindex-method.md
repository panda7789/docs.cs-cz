---
title: ICorDebugVariableSymbol::GetSlotIndex – metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol::GetSlotIndex – metoda
Získá index spravované slotu místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 [out] Ukazatel na místní proměnné pozici indexu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud bylo úspěšné. `E_FAIL` Pokud je proměnná argument funkce.  
  
## <a name="remarks"></a>Poznámky  
 Index spravované slotu místní proměnné lze načíst informace o metadatech proměnné  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
