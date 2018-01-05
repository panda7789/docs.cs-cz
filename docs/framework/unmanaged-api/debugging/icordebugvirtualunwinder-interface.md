---
title: "Rozhraní ICorDebugVirtualUnwinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a>Rozhraní ICorDebugVirtualUnwinder
Poskytuje metody, které pomohou v uvolnění zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Název|  
|------------|----------|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Získá aktuální kontext tento unwinder.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Přejde k kontextu volajícího.|  
  
## <a name="remarks"></a>Poznámky  
 Členové `ICorDebugVirtualUnwinder` rozhraní je implementováno modulem ladicího programu při uvolnění zásobníku.  
  
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
