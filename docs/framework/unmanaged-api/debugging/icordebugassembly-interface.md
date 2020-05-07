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
ms.openlocfilehash: d9e2236b944137de82bb056820f81014febfcc5f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894899"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly – rozhraní

Představuje sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateModules – metoda](icordebugassembly-enumeratemodules-method.md)|Získá enumerátor pro moduly obsažené v sestavení.|  
|[GetAppDomain – metoda](icordebugassembly-getappdomain-method.md)|Získá ukazatel rozhraní na doménu aplikace, která obsahuje tuto `ICorDebugAssembly` instanci.|  
|[GetCodeBase – metoda](icordebugassembly-getcodebase-method.md)|Není implementováno v aktuální verzi .NET Framework.|  
|[GetName – metoda](icordebugassembly-getname-method.md)|Získá název sestavení.|  
|[GetProcess – metoda](icordebugassembly-getprocess-method.md)|Získá instanci ICorDebugProcess, ve které je sestavení spuštěno.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
