---
title: "Rozhraní ICorDebugLoadedModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cc7a36deb7c81ccf67427b833dead7127619b39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodule-interface"></a>Rozhraní ICorDebugLoadedModule
Poskytuje informace o načíst modul.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Získá základní adresu načíst modulu.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Získá název načíst modulu.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Získá velikost v bajtech načíst modul.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugLoadedModule` Rozhraní je implementováno modulem ladicí program a je používána CLR ladění v rozhraní pro získání informací o načíst modul z ladicího programu.  
  
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
