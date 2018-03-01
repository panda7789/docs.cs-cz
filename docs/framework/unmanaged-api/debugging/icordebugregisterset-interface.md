---
title: "ICorDebugRegisterSet – rozhraní"
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
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 714f3d7839ce1d8b65405b6cb3c91d43f1db6642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet – rozhraní
Představuje sadu registrů, k dispozici v počítači, který je aktuálně provádění kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.|  
|[GetRegistersAvailable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Získá trochu maskování, která určuje, který registruje v tomto `ICorDebugRegisterSet` jsou nyní k dispozici.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Získá kontext aktuálního vlákna.|  
|[SetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Není implementována pro rozhraní .NET Framework verze 2.0.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Není implementována pro rozhraní .NET Framework 2.0.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRegisterSet` Rozhraní podporuje pouze 32bitové registry. Použití [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) rozhraní na platformách, které vyžadují další registrů, například IA-64.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
