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
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792074"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet – rozhraní
Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRegisters – metoda](icordebugregisterset-getregisters-method.md)|Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.|  
|[GetRegistersAvailable – metoda](icordebugregisterset-getregistersavailable-method.md)|Načte bitovou masku, která označuje, které Registry v tomto `ICorDebugRegisterSet` jsou aktuálně k dispozici.|  
|[GetThreadContext – metoda](icordebugregisterset-getthreadcontext-method.md)|Získá kontext aktuálního vlákna.|  
|[SetRegisters – metoda](icordebugregisterset-setregisters-method.md)|Není implementováno pro .NET Framework verze 2,0.|  
|[SetThreadContext – metoda](icordebugregisterset-setthreadcontext-method.md)|Není implementováno pro .NET Framework 2,0.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugRegisterSet` podporuje pouze 32 bitové Registry. Použijte rozhraní [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
