---
title: ICorDebugVariableHomeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be1ba87ae979911dd21647569725eafa2c80ffa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080720"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum::Next – metoda
Získá zadaný počet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o lokálních proměnných a argumentů funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Počet objektů, které se mají načíst.  
  
 `homes`  
 Pole ukazatelů, každý z nich odkazuje [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekt, který poskytuje informace o místní proměnné nebo argumentu funkce.  
  
 `pceltFetched`  
 [out] Počet instancí, které skutečně vrácených objektů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí následující hodnoty.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Metoda byla úspěšně dokončena.|  
|`S_FALSE`|Načíst skutečný počet instancí, jak jsou uvedeny v `pceltFetched`, je menší než počet instancí požadavku.|  
  
## <a name="remarks"></a>Poznámky  
 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda načte maximálně `celt` objekty od aktuální pozice čítače výčtu. Po návratu metody `pceltFetched` obsahuje skutečný počet objektů, které jsou načteny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHomeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
