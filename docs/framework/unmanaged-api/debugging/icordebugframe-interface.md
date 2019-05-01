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
ms.openlocfilehash: a15d7f16676b8b9d66f8d1ba7484f3fec5735a44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988751"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame – rozhraní

Představuje snímek aktuálního zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Získá icordebugstepper – k provádění operací krokování vzhledem k to `ICorDebugFrame`.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Získá ukazatel `ICorDebugFrame` v aktuálním řetězci, volá tento rámec, nebo vrátí hodnotu null, pokud je vnitřní rámec v řetězci.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Získá ukazatel `ICorDebugFrame` v aktuálním řetězci, který volá tento rámec nebo vrátí hodnotu null, pokud je nejkrajnější rámce v řetězci.|  
|[GetChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Získá ukazatel icordebugchain – to `ICorDebugFrame` je součástí.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Získá ukazatel na ICorDebugCode přidružené k tento rámec zásobníku.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Získá ukazatel na ICorDebugFunction, která obsahuje kód spojený s rámce zásobníku.|  
|[GetFunctionToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Získá token metadat pro funkci, která obsahuje kód spojený s rámce zásobníku.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Získá absolutní adresu rozsahu bloku zásobníku představovaného tímto rozhraním `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
