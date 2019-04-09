---
title: ICorDebugValueEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9484f211ff31c4fa71692db646ef3c556df0acad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171935"
---
# <a name="icordebugvalueenum-interface"></a>ICorDebugValueEnum – rozhraní
Implementuje metody "ICorDebugEnum" a vytváří výčet polí "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-next-method.md)|Získá zadaný počet `ICorDebugValue` instancí z výčtu od aktuální pozice.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
