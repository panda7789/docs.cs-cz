---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Představuje rámce zásobníku kódu (MSIL intermediate language) společnosti Microsoft. Toto rozhraní je podtřídou třídy rozhraní ICorDebugFrame.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Získá hodnotu, která určuje, zda je bezpečné nastavit ukazatel instrukce do zadaného umístění posunu.|  
|[EnumerateArguments – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Získá enumerátor pro argumenty do tohoto rámce.|  
|[EnumerateLocalVariables – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Získá enumerátor pro místní proměnné do tohoto rámce.|  
|[GetArgument – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Získá hodnotu zadaného argumentu v rámci této MSIL zásobníku.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Získá hodnotu ukazatel instrukce a bitovou kombinaci hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukcí.|  
|[GetLocalVariable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Získá hodnotu zadaného místní proměnné v rámci této MSIL zásobníku.|  
|[GetStackDepth – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Není implementováno.|  
|[GetStackValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Není implementováno.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Nastaví ukazatel instrukce do zadaného umístění posunu v MSIL kódu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugILFrame` Rozhraní je specializovaná ICorDebugFrame rozhraní. Použije se buď MSIL kód rámce nebo v běhu (JIT) zkompilovat rámce. Rámce kompilována implementovat i `ICorDebugILFrame` ICorDebugNativeFrame rozhraní a.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
