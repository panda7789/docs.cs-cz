---
title: ICorDebugStepper – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212515"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper – rozhraní
Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Deactivate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|To způsobí, že `ICorDebugStepper` zrušení poslední krok příkazu získala.|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugStepper` právě probíhá krok.|  
|[SetInterceptMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Cordebugintercept – hodnota, která určuje typy kódu, které jsou vkročili nastaví.|  
|[SetRangeIL – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Nastaví hodnotu určující, zda volání [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předání hodnoty argumentu vzhledem k nativní kód nebo kód Microsoft intermediate language (MSIL) metody, která je právě prošli.|  
|[SetUnmappedStopMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Nastaví hodnotu cordebugunmappedstop –, který určuje typ nenamapované kódu, ve kterém se zastaví provádění.|  
|[Step – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|To způsobí, že `ICorDebugStepper` jedním krokem prostřednictvím jeho nadřazeného vlákna a volitelně do pokračujte v jedné krokování funkcí, které jsou volány vlákna.|  
|[StepOut – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|To způsobí, že `ICorDebugStepper` krokování jeho nadřazeného vlákna a v případě kompletní aktuální rámec vrátí řízení volající rámec.|  
|[StepRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|To způsobí, že `ICorDebugStepper` jedním krokem prostřednictvím jeho nadřazeného vlákna a vrátit se při dosažení kód za poslední zadaný rozsah.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStepper` Rozhraní slouží k těmto účelům:  
  
-   Funguje jako identifikátor mezi kroku příkaz, který je vydaný a dokončení tohoto příkazu.  
  
-   Poskytuje centrální rozhraní k zapouzdření všech krokování, které lze provést.  
  
-   Poskytuje způsob, jak předčasně krokování operaci zrušit.  
  
 Může existovat více než jeden krokovač na vlákno. Například zarážky narazit při krokování přes funkci a uživatel chtít spustit nový krokování operaci uvnitř této funkce. Záleží ladicí program určit, jak tuto situaci. Ladicí program může chtít zrušit původní krokování nebo vnořené dvě operace. `ICorDebugStepper` Rozhraní podporuje obě možnosti.  
  
 Pokud modul CLR (CLR) provede volání více vláken, zařazené krokovač migrovat mezi vlákny.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
