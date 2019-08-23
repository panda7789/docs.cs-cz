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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936996"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame – rozhraní

Představuje snímek aktuálního zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Získá ICorDebugStepper, který provede operace krokování vzhledem k `ICorDebugFrame`tomuto.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Získá ukazatel na `ICorDebugFrame` z aktuálního řetězce, který tento rámec volá, nebo vrátí hodnotu null, pokud se jedná o vnitřní rámec v řetězci.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Získá ukazatel na `ICorDebugFrame` v aktuálním řetězci, který volal tento rámec, nebo vrátí hodnotu null, pokud se jedná o nejvzdálenější rámec v řetězci.|  
|[GetChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Získá ukazatel na ICorDebugChain `ICorDebugFrame` , který je součástí.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Získá ukazatel na ICorDebugCode spojený s tímto rámcem zásobníku.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetFunctionToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Získá token metadat pro funkci, která obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Získá absolutní rozsah adres rámce zásobníku reprezentovaného tímto `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
