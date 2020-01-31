---
title: ICorDebugBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784379"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint – rozhraní

Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Activate – metoda](icordebugbreakpoint-activate-method.md)|Nastaví aktivní stav tohoto `ICorDebugBreakpoint`.|  
|[IsActive – metoda](icordebugbreakpoint-isactive-method.md)|Získá hodnotu, která označuje, zda je tato `ICorDebugBreakpoint` aktivní.|  
  
## <a name="remarks"></a>Poznámky  
 Zarážky přímo nepodporují podmíněné výrazy. Pokud jsou takové funkce žádoucí, ladicí program je musí implementovat nad `ICorDebugBreakpoint`.  
  
 Rozhraní ICorDebugFunctionBreakpoint rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
