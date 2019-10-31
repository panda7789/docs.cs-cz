---
title: ICorDebugRegisterSet2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 47beba867cd2246c98cb02c3a563b948c15f5154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131316"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 – rozhraní
Rozšiřuje možnosti rozhraní [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro hardwarové platformy, které mají více než 64 registrů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.|  
|[GetRegistersAvailable – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Získá pole bajtů, které poskytuje rastrový obrázek dostupných registrů.|  
|[SetRegisters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|Není implementováno v .NET Framework verze 2,0.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
