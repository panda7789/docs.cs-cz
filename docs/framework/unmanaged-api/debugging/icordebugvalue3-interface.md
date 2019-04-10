---
title: ICorDebugValue3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221974"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 – rozhraní
Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSize64 – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|Získá velikost v bajtech, to `ICorDebugValue3` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 [Icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda vrátí objekt velikost, rozsahu od 0 do 2 147 483 647 bajtů. V [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], velikost pole může být delší než 2 GB. `ICorDebugValue3` Rozhraní vám umožní určit velikost těchto polí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
