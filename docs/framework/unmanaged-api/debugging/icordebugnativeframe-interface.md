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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994614"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame – rozhraní

Specializovaná implementace ICorDebugFrame pro nativní snímky.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Získá hodnotu, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu v nativním kódu.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Získá odsazení rámce zásobníku do nativního kódu.|  
|[GetLocalDoubleRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo lokální proměnné uloženy ve dvou paměti registrů, které je nativní rámec.|  
|[GetLocalMemoryRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Získá ukazatel `ICorDebugValue` , který představuje hodnotu místní proměnné, které s nízkou bity jsou uloženy do zadaného registru a vysokou bity jsou uloženy na adrese zadaná paměťová.|  
|[GetLocalMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Získá ukazatel `ICorDebugValue` , který představuje hodnotu lokální proměnné uloženy na adrese zadaná paměťová.|  
|[GetLocalRegisterMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Získá ukazatel `ICorDebugValue` , která představuje hodnotu místní proměnné, které vysokou bity jsou uloženy do zadaného registru a nízkou bity jsou uloženy na adrese zadaná paměťová|  
|[GetLocalRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Získá ukazatel `ICorDebugValue` , který představuje hodnotu argument nebo lokální proměnné uloženy v zadané nativní registru.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Získá ukazatel [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , která představuje do registru, nastavte pro tento `ICorDebugNativeFrame`.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Nastaví ukazatele na instrukci do zadaného umístění posunu v nativním kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
