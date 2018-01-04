---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd49d745be9db0c4c5309cf5febc3ff651a860f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe-interface1"></a>ICorDebugNativeFrame Interface1
Specializovaná implementace ICorDebugFrame používá pro nativní rámce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanSetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Získá hodnotu, která určuje, zda je bezpečné nastavení ukazatel instrukce do zadaného umístění posunu v nativním kódu.|  
|[GetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Získá Posun rámce zásobníku do nativního kódu.|  
|[GetLocalDoubleRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené registry dvě paměti nativní rámce.|  
|[GetLocalMemoryRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Získá odkazy `ICorDebugValue` představující hodnotu místní proměnné, které nízkou bity jsou uloženy v zadané registrace a vysokou bity jsou uloženy v zadané paměti.|  
|[GetLocalMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Získá ukazatel na `ICorDebugValue` představující hodnotu místní proměnné uložené v zadané paměti.|  
|[GetLocalRegisterMemoryValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Získá odkazy `ICorDebugValue` představující hodnotu místní proměnné, které vysoké bity jsou uloženy v zadané registrace a nízkou bity jsou uloženy v zadané paměti|  
|[GetLocalRegisterValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Získá odkazy `ICorDebugValue` představující hodnotu argumentu nebo místní proměnné uložené v zadané nativní registrace.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Získá odkazy [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) představující registrace nastavit pro `ICorDebugNativeFrame`.|  
|[SetIP – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Nastaví ukazatel instrukce do zadaného umístění posunu v nativním kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
