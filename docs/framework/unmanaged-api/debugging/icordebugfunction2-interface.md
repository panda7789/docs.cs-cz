---
title: ICorDebugFunction2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: 5364e39f7e0a9b6c9cd10cd8f17bab4a03a4b7af
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794485"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2 – rozhraní

Logicky rozšiřuje rozhraní ICorDebugFunction, aby poskytovala podporu pro Pouze můj kód krok po ladění, které přeskočí jiný než uživatelský kód.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateNativeCode – metoda](icordebugfunction2-enumeratenativecode-method.md)|(Ještě není implementováno.) Získá ukazatel rozhraní na ICorDebugCodeEnum, který obsahuje příkazy nativního kódu ve funkci, na kterou odkazuje tento objekt ICorDebugFunction2.|  
|[GetJMCStatus – metoda](icordebugfunction2-getjmcstatus-method.md)|Získá hodnotu, která označuje, zda je tato funkce označena jako uživatelský kód.|  
|[GetVersionNumber – metoda](icordebugfunction2-getversionnumber-method.md)|Získá verzi této funkce pro úpravu a pokračování.|  
|[SetJMCStatus – metoda](icordebugfunction2-setjmcstatus-method.md)|Označuje tuto funkci pro Pouze můj kód krokování.|  
  
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
