---
title: "ICorDebugStepper::StepRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange – metoda
Způsobí, že tento ICorDebugStepper jedním krokem prostřednictvím jeho obsahující přístup z více vláken a vrátí, když dorazí do kódu nad rámec poslední zadaný rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bStepIn`  
 [v] Nastavte na `true` k krokování s vnořením funkci, která je volána v rámci vlákno. Nastavte na `false` krok přes funkci.  
  
 `ranges`  
 [v] Pole cor_debug_step_range – struktury, z nichž každý určuje rozsah.  
  
 `cRangeCount`  
 [v] Velikost `ranges` pole.  
  
## <a name="remarks"></a>Poznámky  
 `StepRange` Metoda se dá použít jako [icordebugstepper::Step –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metoda, s tím rozdílem, že dokud kód mimo zadaný rozsah nedokončí bylo dosaženo.  
  
 To může být efektivnější než krokování s jedné instrukce v čase. Rozsahy jsou zadané jako seznam dvojic posunutí od začátku krokovač rámce.  
  
 Rozsahy jsou relativní vzhledem k kód Microsoft (MSIL intermediate language) metody. Volání [icordebugstepper::setrangeil –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) s `false` aby rozsahy relativně k nativní kód metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
