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
ms.openlocfilehash: b92c3d3328c657762ed002155ef4947a9292b19e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894730"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint – rozhraní

Představuje zarážku ve funkci nebo bod sledování na hodnotě.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Activate – metoda](icordebugbreakpoint-activate-method.md)|Nastaví aktivní stav této `ICorDebugBreakpoint`.|  
|[IsActive – metoda](icordebugbreakpoint-isactive-method.md)|Načte hodnotu, která označuje, zda `ICorDebugBreakpoint` je tato hodnota aktivní.|  
  
## <a name="remarks"></a>Poznámky  
 Zarážky přímo nepodporují podmíněné výrazy. Pokud jsou takové funkce žádoucí, ladicí program je musí implementovat nad `ICorDebugBreakpoint`.  
  
 Rozhraní ICorDebugFunctionBreakpoint rozšiřuje `ICorDebugBreakpoint` na podporu zarážek v rámci funkcí.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
