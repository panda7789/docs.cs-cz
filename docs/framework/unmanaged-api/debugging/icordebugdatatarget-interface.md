---
title: ICorDebugDataTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930821"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget – rozhraní
Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPlatform – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Načte blok souvislé paměti začínající na zadané adrese a vrátí ji do zadané vyrovnávací paměti.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Vyžádá aktuální kontext vlákna pro zadané vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugDataTarget`a jeho metody mají následující vlastnosti:  
  
- Metody volání služby ladění v tomto rozhraní pro přístup k paměti a dalším datům v cílovém procesu.  
  
- Klient ladicího programu musí implementovat toto rozhraní v závislosti na konkrétním cíli (například při živém procesu nebo výpisu paměti).  
  
- Metody lze vyvolat pouze v rámci metod implementovaných v jiných `ICorDebug*` rozhraních. `ICorDebugDataTarget` Tím je zajištěno, že klient ladicího programu má kontrolu nad tím, ve kterém vlákně je vyvoláno, a kdy.  
  
- `ICorDebugDataTarget` Implementace musí vždycky vracet aktuální informace o cíli.  
  
 Při `ICorDebug*` volání rozhraní (a tudíž `ICorDebugDataTarget` metod) by se měl cílový proces zastavit a nijak beze změny. Pokud je cílem živý proces a jeho změny stavu, metoda [ICLRDebugging:: OpenVirtualProcess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) musí být znovu volána, aby poskytovala náhradní instanci ICorDebugProcess.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
