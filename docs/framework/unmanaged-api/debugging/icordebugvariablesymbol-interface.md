---
title: "ICorDebugVariableSymbol rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a09fab1468435212c4437c58c113691e049b1ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol rozhraní
Načte informace o ladění symbol pro proměnnou.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|Získá název proměnné.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|Získá velikost proměnné v bajtech.|  
|[GetSlotIndex – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|Získá index spravované slotu místní proměnné.|  
|[GetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|Získá hodnotu proměnné jako bajtové pole.|  
|[SetValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|Proměnné přiřazuje hodnoty bajtové pole.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní je k dispozici s .NET Native jenom. Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
