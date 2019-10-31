---
title: ICorDebugChain – rozhraní
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
ms.openlocfilehash: 8baf3567e4ae188f88ad3a2df157cffab3f597ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125802"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain – rozhraní

Představuje segment fyzického nebo logického zásobníku volání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateFrames – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Získá enumerátor, který obsahuje všechny spravované rámce zásobníku v řetězci počínaje posledním rámcem.|  
|[GetActiveFrame – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Získá aktivní (tj. poslední) rámec v řetězu.|  
|[GetCallee – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Získá řetězec, který byl volán tímto řetězem.|  
|[GetCaller – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Získá řetězec, který se nazývá tento řetězec.|  
|[GetContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Není implementováno.|  
|[GetNext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Získá další řetězec snímků pro vlákno.|  
|[GetPrevious – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Načte předchozí řetězec snímků pro vlákno.|  
|[GetReason – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Získá důvod pro Genesis tohoto volajícího řetězu.|  
|[GetRegisterSet – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Načte sadu registrů pro aktivní část tohoto řetězu.|  
|[GetStackRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Získá rozsah adres segmentu zásobníku pro tento řetěz.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Získá fyzické vlákno, na kterém je tento řetěz volání součástí.|  
|[IsManaged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Získá hodnotu, která označuje, zda je v tomto řetězci spuštěn spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Rámce zásobníku v řetězu zabírají souvislý prostor zásobníku a sdílejí stejné vlákno a kontext. Řetěz může představovat buď spravované nebo nespravované řetězy kódu. Prázdná instance `ICorDebugChain` představuje řetězec nespravovaného kódu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
