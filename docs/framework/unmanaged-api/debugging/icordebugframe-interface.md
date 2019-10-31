---
title: ICorDebugFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124064"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame – rozhraní

Představuje snímek aktuálního zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Získá ICorDebugStepper, který provede operace krokování vzhledem k tomuto `ICorDebugFrame`.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Získá ukazatel na `ICorDebugFrame` v aktuálním řetězu, který tento rámec volal, nebo vrátí hodnotu null, pokud se jedná o nejvnitřnější rámec v řetězci.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Získá ukazatel na `ICorDebugFrame` v aktuálním řetězci, který volal tento rámec, nebo vrátí hodnotu null, pokud se jedná o nejvzdálenější rámec v řetězci.|  
|[GetChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Získá ukazatel na ICorDebugChain, který je součástí tohoto `ICorDebugFrame`.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Získá ukazatel na ICorDebugCode spojený s tímto rámcem zásobníku.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetFunctionToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Získá token metadat pro funkci, která obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Získá absolutní rozsah adres rámce zásobníku reprezentovaného tímto `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
