---
title: ICorDebugHeapValue3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: ddfe8cee8fdbca910ffa4f6989b1359ae5f7b11f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794373"
---
# <a name="icordebugheapvalue3-interface"></a>ICorDebugHeapValue3 – rozhraní
Zpřístupní vlastnosti uzamčení sledování objektů. Toto rozhraní rozšiřuje rozhraní ICorDebugHeapValue a ICorDebugHeapValue2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetThreadOwningMonitorLock – metoda](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.|  
|[GetMonitorEventWaitList – metoda](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|Poskytuje uspořádaný seznam vláken, která jsou zařazená do fronty pro událost přidruženou ke zámku monitoru.|  
  
## <a name="remarks"></a>Poznámky  
  
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
