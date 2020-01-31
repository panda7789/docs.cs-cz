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
ms.openlocfilehash: e9bb69567a247472af42efb08b609d3474c87ed2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791795"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper – rozhraní
Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Deactivate – metoda](icordebugstepper-deactivate-method.md)|Způsobí, že toto `ICorDebugStepper` zruší přijatý příkaz posledního kroku.|  
|[IsActive – metoda](icordebugstepper-isactive-method.md)|Získá hodnotu, která označuje, zda tento `ICorDebugStepper` aktuálně provádí krok.|  
|[SetInterceptMask – metoda](icordebugstepper-setinterceptmask-method.md)|Nastaví hodnotu CorDebugIntercept –, která určuje typy kódu, na které se používá.|  
|[SetRangeIL – metoda](icordebugstepper-setrangeil-method.md)|Nastaví hodnotu, která označuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentu relativně k nativnímu kódu nebo kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.|  
|[SetUnmappedStopMask – metoda](icordebugstepper-setunmappedstopmask-method.md)|Nastaví hodnotu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.|  
|[Step – metoda](icordebugstepper-step-method.md)|Způsobí, že se toto `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna, a volitelně, aby bylo možné pokračovat v jednoduchém krokování prostřednictvím funkcí, které jsou volány ve vlákně.|  
|[StepOut – metoda](icordebugstepper-stepout-method.md)|Způsobí, že se tato `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna a k dokončení, když aktuální rámec vrátí řízení volajícímu snímku.|  
|[StepRange – metoda](icordebugstepper-steprange-method.md)|Způsobí, že se tato `ICorDebugStepper` k jednomu kroku prostřednictvím jeho obsahujícího vlákna a vrátí se, pokud dosáhne kódu za poslední z určených rozsahů.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugStepper` slouží k následujícím účelům:  
  
- Funguje jako identifikátor mezi příkazem kroku, který je vydán a dokončením tohoto příkazu.  
  
- Poskytuje centrální rozhraní pro zapouzdření veškerého krokování, které je možné provést.  
  
- Poskytuje způsob, jak předčasně zrušit operaci krokování.  
  
 Na vlákno může být více než jeden stepper. Například zarážka může být dosaženo při krokování nad funkcí a uživatel může chtít spustit novou operaci krokování uvnitř této funkce. Aby bylo možné určit, jak se má tato situace zvládnout, je k ladicí program. Ladicí program může chtít zrušit původní operaci krokování nebo vnořit tyto dvě operace. Rozhraní `ICorDebugStepper` podporuje obě volby.  
  
 Stepper se může migrovat mezi vlákny, pokud modul CLR (Common Language Runtime) provede více vláken, zařaditelné volání.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
