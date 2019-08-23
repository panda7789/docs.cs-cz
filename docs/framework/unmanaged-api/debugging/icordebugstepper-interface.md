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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962690"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper – rozhraní
Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Deactivate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Způsobí zrušení příkazu posledního kroku, kterýpřijal.`ICorDebugStepper`|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Načte hodnotu, která označuje, zda `ICorDebugStepper` se aktuálně provádí krok.|  
|[SetInterceptMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Nastaví hodnotu CorDebugIntercept –, která určuje typy kódu, na které se používá.|  
|[SetRangeIL – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Nastaví hodnotu, která označuje, zda volání [ICorDebugStepper:: StepRange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předávají hodnoty argumentu relativně k nativnímu kódu nebo kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.|  
|[SetUnmappedStopMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Nastaví hodnotu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.|  
|[Step – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím jeho nadřazeného vlákna a volitelně pro pokračování v jednoduchém provádění prostřednictvím funkcí, které jsou volány v rámci vlákna.|  
|[StepOut – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím obsahujícího vlákna a k dokončení, když aktuální rámec vrátí řízení volajícímu snímku.|  
|[StepRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím obsahujícího vlákna a vrátí se, když dosáhne kódu nad poslední z určených rozsahů.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStepper` Rozhraní slouží k následujícím účelům:  
  
- Funguje jako identifikátor mezi příkazem kroku, který je vydán a dokončením tohoto příkazu.  
  
- Poskytuje centrální rozhraní pro zapouzdření veškerého krokování, které je možné provést.  
  
- Poskytuje způsob, jak předčasně zrušit operaci krokování.  
  
 Na vlákno může být více než jeden stepper. Například zarážka může být dosaženo při krokování nad funkcí a uživatel může chtít spustit novou operaci krokování uvnitř této funkce. Aby bylo možné určit, jak se má tato situace zvládnout, je k ladicí program. Ladicí program může chtít zrušit původní operaci krokování nebo vnořit tyto dvě operace. `ICorDebugStepper` Rozhraní podporuje obě volby.  
  
 Stepper se může migrovat mezi vlákny, pokud modul CLR (Common Language Runtime) provede více vláken, zařaditelné volání.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
