---
title: ICorDebugCode4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 870ac1e62363493989fe638483ea474d648c8c69
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893309"
---
# <a name="icordebugcode4-interface"></a>ICorDebugCode4 – rozhraní
Poskytuje metodu, která umožňuje ladicímu programu vytvořit výčet místních proměnných a argumentů ve funkci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateVariableHomes – metoda](icordebugcode4-enumeratevariablehomes-method.md)|Získá enumerátor pro místní proměnné a argumenty ve funkci.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
