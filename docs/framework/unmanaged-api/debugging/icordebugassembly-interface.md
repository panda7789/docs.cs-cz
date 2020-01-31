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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784676"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly – rozhraní

Představuje sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateModules – metoda](icordebugassembly-enumeratemodules-method.md)|Získá enumerátor pro moduly obsažené v sestavení.|  
|[GetAppDomain – metoda](icordebugassembly-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto instanci `ICorDebugAssembly`.|  
|[GetCodeBase – metoda](icordebugassembly-getcodebase-method.md)|Není implementováno v aktuální verzi .NET Framework.|  
|[GetName – metoda](icordebugassembly-getname-method.md)|Získá název sestavení.|  
|[GetProcess – metoda](icordebugassembly-getprocess-method.md)|Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
