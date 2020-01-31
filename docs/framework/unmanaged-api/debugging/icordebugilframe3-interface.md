---
title: ICorDebugILFrame3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 739c648173d45a9c147ea2a4e469a3a4b518e893
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794339"
---
# <a name="icordebugilframe3-interface"></a>ICorDebugILFrame3 – rozhraní
Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce. `ICorDebugILFrame3` je logické rozšíření rozhraní ICorDebugILFrame a ICorDebugILFrame2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReturnValueForILOffset – metoda](icordebugilframe3-getreturnvalueforiloffset-method.md)|Získá objekt ICorDebugValue, který zapouzdřuje vrácenou hodnotu funkce.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
