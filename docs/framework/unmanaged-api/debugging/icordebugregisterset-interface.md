---
title: "ICorDebugRegisterSet – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet – rozhraní
Představuje sadu registrů, k dispozici v počítači, který je aktuálně provádění kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getregisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.|  
|[Getregistersavailable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Získá trochu maskování, která určuje, který registruje v tomto `ICorDebugRegisterSet` jsou nyní k dispozici.|  
|[Getthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Získá kontext aktuálního vlákna.|  
|[Setregisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Není implementována pro rozhraní .NET Framework verze 2.0.|  
|[Setthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Není implementována pro rozhraní .NET Framework 2.0.|  
  
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
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet2 – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
