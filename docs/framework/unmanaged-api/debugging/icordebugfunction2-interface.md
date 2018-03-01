---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a>ICorDebugFunction2 Interface1
Logicky rozšiřuje rozhraní ICorDebugFunction kvůli zajištění podpory pro pouze můj kód procházení po kroku ladění, který přeskočí bez uživatelského kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateNativeCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(Ještě nebyla implementována.) Získá ukazatele rozhraní umožňuje icordebugcodeenum –, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt ICorDebugFunction2.|  
|[GetJMCStatus – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|Získá hodnotu, která určuje, zda tato funkce je označen jako uživatelského kódu.|  
|[GetVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|Získá verzi aplikace upravit a pokračovat v této funkce.|  
|[SetJMCStatus – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|Tato funkce se pro pouze můj kód označí krokování s.|  
  
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
