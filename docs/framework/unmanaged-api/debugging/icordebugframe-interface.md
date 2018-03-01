---
title: ICorDebugFrame Interface1
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
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a>ICorDebugFrame Interface1
Představuje snímek aktuálního zásobníku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateStepper – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Získá ICorDebugStepper k provádění operací taktování relativně k to `ICorDebugFrame`.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Získá odkazy `ICorDebugFrame` v řetězu aktuální volá tento rámečku, nebo vrátí hodnotu null, pokud je nejvnitřnější rámečku v řetězci.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Získá odkazy `ICorDebugFrame` v řetězu aktuální, který je volán tohoto rámce nebo vrátí hodnotu null, pokud je nejkrajnější rámečku v řetězci.|  
|[GetChain – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Získá odkazy ICorDebugChain tento `ICorDebugFrame` je součástí.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Získá ukazatel na ICorDebugCode přidružené k této rámce zásobníku.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s Tento rámce zásobníku.|  
|[GetFunctionToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Získá metadata token pro funkce, která obsahuje kód přidružené k této rámce zásobníku.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Získá absolutní adresu rozsahu rámce zásobníku reprezentována to `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
