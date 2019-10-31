---
title: ICorDebugComObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125491"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue – rozhraní
Poskytuje metody pro načtení informací spojených s vydaným obálkou pro spuštění v modulu runtime (RCW).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCachedInterfacePointers – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Načte nezpracované ukazatele rozhraní v mezipaměti v aktuální RCW.|  
|[GetCachedInterfaceTypes – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Poskytuje enumerátor pro typy rozhraní, pro které byl aktuální objekt použita nebo použit jako.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li ověřit, zda instance rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` v "ICorDebugValue" s `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
