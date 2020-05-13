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
ms.openlocfilehash: 622fdfa37c93e406950e73941775828ae4b112fa
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379425"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper – rozhraní
Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Deactivate – metoda](icordebugstepper-deactivate-method.md)|Způsobí `ICorDebugStepper` zrušení příkazu posledního kroku, který přijal.|  
|[IsActive – metoda](icordebugstepper-isactive-method.md)|Načte hodnotu, která označuje, zda `ICorDebugStepper` se aktuálně provádí krok.|  
|[SetInterceptMask – metoda](icordebugstepper-setinterceptmask-method.md)|Nastaví hodnotu CorDebugIntercept –, která určuje typy kódu, na které se používá.|  
|[SetRangeIL – metoda](icordebugstepper-setrangeil-method.md)|Nastaví hodnotu, která označuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentu relativně k nativnímu kódu nebo kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.|  
|[SetUnmappedStopMask – metoda](icordebugstepper-setunmappedstopmask-method.md)|Nastaví hodnotu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.|  
|[Step – metoda](icordebugstepper-step-method.md)|Způsobí, `ICorDebugStepper` že se jedná o krok do jednoho kroku prostřednictvím jeho nadřazeného vlákna a volitelně pro pokračování v jednoduchém provádění prostřednictvím funkcí, které jsou volány v rámci vlákna.|  
|[StepOut – metoda](icordebugstepper-stepout-method.md)|Způsobí, že se jedná `ICorDebugStepper` o krok do jednoho kroku prostřednictvím obsahujícího vlákna a k dokončení, když aktuální rámec vrátí řízení volajícímu snímku.|  
|[StepRange – metoda](icordebugstepper-steprange-method.md)|Způsobí, že se jedná `ICorDebugStepper` o krok do jednoho kroku prostřednictvím obsahujícího vlákna a vrátí se, když dosáhne kódu nad poslední z určených rozsahů.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStepper`Rozhraní slouží k následujícím účelům:  
  
- Funguje jako identifikátor mezi příkazem kroku, který je vydán a dokončením tohoto příkazu.  
  
- Poskytuje centrální rozhraní pro zapouzdření veškerého krokování, které je možné provést.  
  
- Poskytuje způsob, jak předčasně zrušit operaci krokování.  
  
 Na vlákno může být více než jeden stepper. Například zarážka může být dosaženo při krokování nad funkcí a uživatel může chtít spustit novou operaci krokování uvnitř této funkce. Aby bylo možné určit, jak se má tato situace zvládnout, je k ladicí program. Ladicí program může chtít zrušit původní operaci krokování nebo vnořit tyto dvě operace. `ICorDebugStepper`Rozhraní podporuje obě volby.  
  
 Stepper se může migrovat mezi vlákny, pokud modul CLR (Common Language Runtime) provede více vláken, zařaditelné volání.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
