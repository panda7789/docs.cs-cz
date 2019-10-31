---
title: Rozhraní ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 9c1a5cde5a39a334d655d865c5e44a5eb0c1766a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131045"
---
# <a name="icordebugilcode2-interface"></a>Rozhraní ICorDebugILCode2
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Logicky rozšiřuje rozhraní [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) a poskytuje metody, které vracejí token pro místní proměnnou funkce a které mapují posuny instrumentované zprostředkujícího jazyka (IL) profileru na původní posunutí metody Il.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetInstrumentedILMap – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|Vrátí mapu ze vah instrumentované úrovně IL v profileru na původní posunutí metody IL pro tuto instanci.|  
|[GetLocalVarSigToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|Získá token metadat pro podpis místní proměnné pro funkci, která je reprezentovaná touto instancí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugILCode – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
