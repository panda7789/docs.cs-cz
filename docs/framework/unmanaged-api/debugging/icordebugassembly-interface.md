---
title: ICorDebugAssembly – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426269d14992ae0f1f8c02619b259cfdd4bcbf8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959444"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly – rozhraní

Představuje sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateModules – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Získá enumerátor pro moduly obsažené v sestavení.|  
|[GetAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto `ICorDebugAssembly` instanci.|  
|[GetCodeBase – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|Není implementováno v aktuální verzi .NET Framework.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Získá název sestavení.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
