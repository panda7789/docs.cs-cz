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
ms.openlocfilehash: 528db447df4d71d67441b05ad29e6a900c59afbb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892826"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue – rozhraní
Poskytuje metody pro načtení informací spojených s vydaným obálkou pro spuštění v modulu runtime (RCW).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCachedInterfacePointers – metoda](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Načte nezpracované ukazatele rozhraní v mezipaměti v aktuální RCW.|  
|[GetCachedInterfaceTypes – metoda](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Poskytuje enumerátor pro typy rozhraní, pro které byl aktuální objekt použita nebo použit jako.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li ověřit, zda instance rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` "ICorDebugValue" s. `IID_ICorDebugComObjectValue`  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
