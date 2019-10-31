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
ms.openlocfilehash: 1f46866a1b975455acd294221e38ef3b4c358660
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140203"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 – rozhraní
Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" tak, aby poskytovala podporu pro pole, která jsou větší než 2 GB.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSize64 – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|Získá velikost objektu `ICorDebugValue3` v bajtech.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) vrátí velikost objektu, který je v rozsahu od 0 do 2 147 483 647 bajtů. V .NET Framework 4,5 může velikost polí překročit 2 GB. Rozhraní `ICorDebugValue3` umožňuje určit velikost těchto polí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
