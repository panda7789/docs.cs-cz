---
title: ICorDebugILFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917024"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame – rozhraní

Představuje rámec zásobníku kódu jazyka MSIL (Microsoft Intermediate Language). Toto rozhraní je podtřídou rozhraní ICorDebugFrame.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na určené místo posunutí.|  
|[EnumerateArguments – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Získá enumerátor pro argumenty v tomto snímku.|  
|[EnumerateLocalVariables – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Získá enumerátor pro místní proměnné v tomto snímku.|  
|[GetArgument – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Získá hodnotu zadaného argumentu v rámci tohoto bloku zásobníku MSIL.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.|  
|[GetLocalVariable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Získá hodnotu zadané místní proměnné v tomto bloku zásobníku MSIL.|  
|[GetStackDepth – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Není implementováno.|  
|[GetStackValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Není implementováno.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugILFrame` Rozhraní je specializované rozhraní ICorDebugFrame. Používá se buď pro rámečky kódu MSIL, nebo pro zkompilované snímky JIT (just-in-time). Rámce zkompilované JIT implementují `ICorDebugILFrame` rozhraní i rozhraní ICorDebugNativeFrame.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
