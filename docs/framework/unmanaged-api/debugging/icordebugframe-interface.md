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
ms.openlocfilehash: ba138e79e0d6fb6f9c5e9c3efe3466f3c88cccae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782620"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame – rozhraní

Představuje snímek aktuálního zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStepper – metoda](icordebugframe-createstepper-method.md)|Získá ICorDebugStepper, který provede operace krokování vzhledem k tomuto `ICorDebugFrame`.|  
|[GetCallee – metoda](icordebugframe-getcallee-method.md)|Získá ukazatel na `ICorDebugFrame` v aktuálním řetězu, který tento rámec volal, nebo vrátí hodnotu null, pokud se jedná o nejvnitřnější rámec v řetězci.|  
|[GetCaller – metoda](icordebugframe-getcaller-method.md)|Získá ukazatel na `ICorDebugFrame` v aktuálním řetězci, který volal tento rámec, nebo vrátí hodnotu null, pokud se jedná o nejvzdálenější rámec v řetězci.|  
|[GetChain – metoda](icordebugframe-getchain-method.md)|Získá ukazatel na ICorDebugChain, který je součástí tohoto `ICorDebugFrame`.|  
|[GetCode – metoda](icordebugframe-getcode-method.md)|Získá ukazatel na ICorDebugCode spojený s tímto rámcem zásobníku.|  
|[GetFunction – metoda](icordebugframe-getfunction-method.md)|Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetFunctionToken – metoda](icordebugframe-getfunctiontoken-method.md)|Získá token metadat pro funkci, která obsahuje kód spojený s tímto rámcem zásobníku.|  
|[GetStackRange – metoda](icordebugframe-getstackrange-method.md)|Získá absolutní rozsah adres rámce zásobníku reprezentovaného tímto `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
