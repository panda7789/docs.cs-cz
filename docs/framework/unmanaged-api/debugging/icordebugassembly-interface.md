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
ms.openlocfilehash: a2b802845e36e818a962484c1fea09cbcc1ceefd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974572"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly – rozhraní

Představuje sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateModules – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Získá enumerátor pro moduly, které jsou obsaženy v sestavení.|  
|[GetAppDomain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Získá ukazatel rozhraní k doméně aplikace, která obsahuje tato `ICorDebugAssembly` instance.|  
|[GetCodeBase – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|Není implementováno v aktuální verzi rozhraní .NET Framework.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Získá název sestavení.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Získá instanci ICorDebugProcess, ve kterém je spuštěna sestavení.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
