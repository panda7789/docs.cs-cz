---
title: ICorDebugValue Interface1
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
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a>ICorDebugValue Interface1
Reprezentuje hodnotu v procesu laděné. Hodnota může být pro čtení nebo zápisu hodnotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Tato metoda není implementována aktuálně.|  
|[GetAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Získá adresu tohoto `ICorDebugValue` objekt, který je právě probíhá ladit.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Získá velikost v bajtech to `ICorDebugValue` objektu.|  
|[GetType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Získá primitivní typ tohoto objektu `ICorDebugValue` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí vlastnictví objekt hodnoty se předá, když se vrátí. Pro odebrání odkaz z objektu po dokončení s daným objektem zodpovídá příjemce.  
  
 V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po dokončení opravy. Ano, obecně hodnota by neměla uchovávat prostřednictvím volání z [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
    
    
    
 [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
