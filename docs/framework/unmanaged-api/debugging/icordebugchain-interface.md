---
title: ICorDebugChain Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bb716f1ad4087642a76dc84266ec6d3f46c1ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571201"
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain Interface1
Představuje segment fyzického nebo logického zásobníku volání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateFrames – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaného v řetězci, od posledního rámce.|  
|[GetActiveFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Získá aktivní (to znamená nejnovější) rámce v řetězu.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Získá řetězec, který byl volán tento řetězec.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Získá řetězec, který volá tento řetězec.|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Není implementováno.|  
|[GetNext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Získá další řetězec rámce pro vlákno.|  
|[GetPrevious – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Získá předchozí řetězu rámce pro vlákno.|  
|[GetReason – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Získá důvod genesis tento řetěz volání.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Získá do registru pro aktivní součástí tohoto řetězce.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Získá rozsah adres segmentu zásobníku pro tento řetězec.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Získá fyzické vlákno, které tento řetěz volání je součástí.|  
|[IsManaged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Získá hodnotu určující, zda tento řetězec používá spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Rámce zásobníku v řetězci zabírají prostor souvislých zásobníku a sdílejí stejný vlákna a kontext. Řetězec může představovat buď řetězy spravovaného i nespravovaného kódu. Prázdná `ICorDebugChain` instance představuje řetěz nespravovaného kódu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
