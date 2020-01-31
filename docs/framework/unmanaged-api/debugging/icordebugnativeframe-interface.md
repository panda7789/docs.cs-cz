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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792792"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame – rozhraní

Specializovaná implementace ICorDebugFrame používaná pro nativní rámce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](icordebugnativeframe-cansetip-method.md)|Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané umístění posunu v nativním kódu.|  
|[GetIP – metoda](icordebugnativeframe-getip-method.md)|Získá posun rámce zásobníku do nativního kódu.|  
|[GetLocalDoubleRegisterValue – metoda](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené ve dvou registrech paměti nativního rámce.|  
|[GetLocalMemoryRegisterValue – metoda](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy nízké bity a vysoké bity jsou uloženy na zadané adrese paměti.|  
|[GetLocalMemoryValue – metoda](icordebugnativeframe-getlocalmemoryvalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné uložené v zadané adrese paměti.|  
|[GetLocalRegisterMemoryValue – metoda](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Získá ukazatel na `ICorDebugValue`, který představuje hodnotu místní proměnné, jejíž horní bity jsou uloženy v zadaném registru a dolní bity jsou uloženy na zadané adrese paměti.|  
|[GetLocalRegisterValue – metoda](icordebugnativeframe-getlocalregistervalue-method.md)|Získá ukazatel na `ICorDebugValue`, která představuje hodnotu argumentu nebo místní proměnnou uloženou v zadaném nativním registru.|  
|[GetRegisterSet – metoda](icordebugnativeframe-getregisterset-method.md)|Získá ukazatel na [ICorDebugRegisterSet](icordebugregisterset-interface.md) , který představuje sadu registru pro tento `ICorDebugNativeFrame`.|  
|[SetIP – metoda](icordebugnativeframe-setip-method.md)|Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
