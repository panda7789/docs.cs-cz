---
title: ICorDebugThread4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 0bb25d060853abb20316a344bae3755b2f8b4dc7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791339"
---
# <a name="icordebugthread4-interface"></a>ICorDebugThread4 – rozhraní
Poskytuje informace o blokování vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBlockingObjects – metoda](icordebugthread4-getblockingobjects-method.md)|Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.|  
|[HadUnhandledException – metoda](icordebugthread4-hadunhandledexception-method.md)|Označuje, zda má vlákno někdy neošetřenou výjimku.|  
|[GetCurrentCustomDebuggerNotification – metoda](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je logické rozšíření rozhraní ICorDebugThread, ICorDebugThread2 a [ICorDebugThread3](icordebugthread3-interface.md) .  
  
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
