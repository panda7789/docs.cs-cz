---
title: ICorDebugNativeFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 04bdbc49217236bc6c05a718cb4d42067cafd8bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096677"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame – rozhraní

Specializovaná implementace ICorDebugFrame používaná pro nativní rámce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané umístění posunu v nativním kódu.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Získá posun rámce zásobníku do nativního kódu.|  
|[GetLocalDoubleRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené ve dvou registrech paměti nativního rámce.|  
|[GetLocalMemoryRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy nízké bity a vysoké bity jsou uloženy na zadané adrese paměti.|  
|[GetLocalMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné uložené v zadané adrese paměti.|  
|[GetLocalRegisterMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Získá ukazatel na `ICorDebugValue`, který představuje hodnotu místní proměnné, jejíž horní bity jsou uloženy v zadaném registru a dolní bity jsou uloženy na zadané adrese paměti.|  
|[GetLocalRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu argumentu nebo místní proměnnou uloženou v zadaném nativním registru.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Získá ukazatel na [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , který představuje sadu registru pro tento `ICorDebugNativeFrame`.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
