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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378274"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet – rozhraní
Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRegisters – metoda](icordebugregisterset-getregisters-method.md)|Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.|  
|[GetRegistersAvailable – metoda](icordebugregisterset-getregistersavailable-method.md)|Načte bitovou masku, která označuje, které Registry v této `ICorDebugRegisterSet` době jsou aktuálně k dispozici.|  
|[GetThreadContext – metoda](icordebugregisterset-getthreadcontext-method.md)|Získá kontext aktuálního vlákna.|  
|[SetRegisters – metoda](icordebugregisterset-setregisters-method.md)|Není implementováno pro .NET Framework verze 2,0.|  
|[SetThreadContext – metoda](icordebugregisterset-setthreadcontext-method.md)|Není implementováno pro .NET Framework 2,0.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugRegisterSet`Rozhraní podporuje pouze 32 bitové Registry. Použijte rozhraní [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
