---
title: ICorDebugStackWalk – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378910"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk – rozhraní
Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetContext – metoda](icordebugstackwalk-getcontext-method.md)|Vrátí kontext pro aktuální rámec v `ICorDebugStackWalk` objektu.|  
|[SetContext – metoda](icordebugstackwalk-setcontext-method.md)|Nastaví `ICorDebugStackWalk` aktuální kontext objektu na platný kontext pro vlákno.|  
|[Next – metoda](icordebugstackwalk-next-method.md)|Přesune `ICorDebugStackWalk` objekt k dalšímu snímku.|  
|[GetFrame – metoda](icordebugstackwalk-getframe-method.md)|Získá aktuální rámec v `ICorDebugStackWalk` objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
