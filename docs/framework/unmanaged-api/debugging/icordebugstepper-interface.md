---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper
helpviewer_keywords: ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266e8c664ac7c5efa1b199efc522f0b890e38e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper Interface1
Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Deactivate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|To způsobí, že `ICorDebugStepper` zrušení poslední krok příkazu přijala.|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugStepper` právě probíhá krok.|  
|[SetInterceptMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Nastaví CorDebugIntercept hodnotu, která určuje typy kód, který se stupeň do.|  
|[SetRangeIL – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Nastaví hodnotu určující, zda volá, aby se [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předat hodnoty argumentu relativně k nativní kód nebo kód (MSIL intermediate language) Microsoft metody, která je se provedl.|  
|[SetUnmappedStopMask – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Nastaví CorDebugUnmappedStop hodnotu, která určuje typ nenamapovaný kódu, ve kterém se zastaví provádění.|  
|[Step – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|To způsobí, že `ICorDebugStepper` jedním krokem přes jeho obsahující vláken a volitelně můžete do pokračovat jedním procházení funkce, které se nazývají vlákna.|  
|[StepOut – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|To způsobí, že `ICorDebugStepper` krokování prostřednictvím jeho obsahující vláken a dokončení v případě aktuální rámec vrátí prvek na snímek, volání.|  
|[StepRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|To způsobí, že `ICorDebugStepper` jedním krokem přes jeho obsahující vláken a vrátit, když dorazí do kódu nad rámec poslední zadaný rozsah.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStepper` Rozhraní slouží k těmto účelům:  
  
-   Jedná jako identifikátor mezi krok příkaz, který je vydán a tento příkaz dokončit.  
  
-   Poskytuje centrální rozhraní pro zapouzdření všechny krokování, které lze provést.  
  
-   Poskytuje způsob, jak předčasně zrušit taktování operaci.  
  
 Může existovat více než jeden krokovač na vlákno. Například zarážky narazit při krokování přes funkci a uživatel může chtít spustit operaci nového taktování uvnitř této funkce. Je ladicího programu určit, jak tuto situaci můžete vyřešit. Ladicí program chtít zrušte původní taktování operaci nebo vnořit těchto dvou operací. `ICorDebugStepper` Rozhraní podporuje obě možnosti.  
  
 Je-li krokovač může migrovat mezi vlákny, pokud modul CLR (CLR) zavolá cross-threaded, zařazené.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
