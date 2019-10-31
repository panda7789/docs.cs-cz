---
title: ICorDebugRegisterSet – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 1ea0274adc12f3a99df0422bfc0b5180f0ef5596
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131382"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet – rozhraní
Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.|  
|[GetRegistersAvailable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Načte bitovou masku, která označuje, které Registry v tomto `ICorDebugRegisterSet` jsou aktuálně k dispozici.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Získá kontext aktuálního vlákna.|  
|[SetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Není implementováno pro .NET Framework verze 2,0.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Není implementováno pro .NET Framework 2,0.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugRegisterSet` podporuje pouze 32 bitové Registry. Použijte rozhraní [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
