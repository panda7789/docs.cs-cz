---
title: ICorDebugThread3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791381"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 – rozhraní
Poskytuje vstupní bod pro [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStackWalk – metoda](icordebugthread3-createstackwalk-method.md)|Vytvoří objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.|  
|[GetActiveInternalFrames – metoda](icordebugthread3-getactiveinternalframes-method.md)|Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugThread3` je logické rozšíření rozhraní ICorDebugThread.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
