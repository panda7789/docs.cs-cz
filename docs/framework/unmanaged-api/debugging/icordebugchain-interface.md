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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969295"
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
 Rámce zásobníku v řetězu zabírají souvislý prostor zásobníku a sdílejí stejné vlákno a kontext. Řetěz může představovat buď spravované nebo nespravované řetězy kódu. Prázdná `ICorDebugChain` instance reprezentuje řetězec nespravovaného kódu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
