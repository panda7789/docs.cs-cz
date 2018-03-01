---
title: ICorDebugChain Interface1
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
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain Interface1
Představuje segment fyzického nebo logického zásobníku volání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateFrames – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaných v řetězu, počínaje nejnovější rámečku.|  
|[GetActiveFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Získá aktivní (tedy poslední) rámce v řetězu.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Získá řetězec, který byl volány tento řetězec.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Získá řetězec, který volá tento řetězec.|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Není implementováno.|  
|[GetNext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Získá další řetěz snímků pro vlákno.|  
|[GetPrevious – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Získá předchozí řetěz snímků pro vlákno.|  
|[GetReason – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Získá důvod genesis toto volání řetězu.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Získá zaregistrovat, nastavte pro aktivní součástí tohoto řetězce.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Získá rozsah adres segmentu zásobníku pro tento řetězec.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Získá fyzické vlákno, které je tento řetězec volání součástí.|  
|[IsManaged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Získá hodnotu, která určuje, zda tento řetězec používá spravovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Rámce zásobníku v řetězu zabírají místa na souvislý zásobníku a sdílejí stejný přístup z více vláken a kontext. Řetěz může představovat buď řetězy kód spravované nebo nespravované. Prázdná `ICorDebugChain` instance představuje řetězec nespravovaného kódu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
