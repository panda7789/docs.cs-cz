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
ms.openlocfilehash: 1c60d7685de1e9a1d4f631ad1fba53b981829f58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159794"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame – rozhraní

Představuje rámec zásobníku kódu Microsoft intermediate language (MSIL). Toto rozhraní je podtřídou třídy icordebugframe – rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Získá hodnotu, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu.|  
|[EnumerateArguments – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Získá enumerátor pro argumenty v tomto snímku.|  
|[EnumerateLocalVariables – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Získá enumerátor pro místní proměnné v tomto snímku.|  
|[GetArgument – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Získá hodnotu zadaného argumentu do tohoto rámce zásobníku jazyka MSIL.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Získá hodnotu ukazatele na instrukci a bitová kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele na instrukci.|  
|[GetLocalVariable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Získá hodnotu místní proměnné zadané v rámce zásobníku jazyka MSIL.|  
|[GetStackDepth – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Není implementováno.|  
|[GetStackValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Není implementováno.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Nastaví ukazatele na instrukci do zadaného umístění posunu v kódu MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugILFrame` Rozhraní je specializované icordebugframe – rozhraní. Používá se pro snímky kód jazyka MSIL nebo just-in-time (JIT) zkompilována snímků. Snímky zkompilovaný pomocí kompilátoru JIT implementovat oba `ICorDebugILFrame` icordebugnativeframe – rozhraní a interface.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
