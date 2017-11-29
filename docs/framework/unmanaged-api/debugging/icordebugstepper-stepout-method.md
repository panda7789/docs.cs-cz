---
title: "ICorDebugStepper::StepOut – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut – metoda
Způsobí, že tento ICorDebugStepper jedním krokem přes jeho obsahující vláken a provést při aktuální rámec vrátí prvek na snímek, volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Poznámky  
 A `StepOut` operace dokončí po návratu normálně aktuální rámec volání rámečku.  
  
 Pokud `StepOut` je volána, když v nespravovaném kódu krok dokončí, když se vrátí aktuální rámec do spravovaného kódu, která je volána.  
  
 V rozhraní .NET Framework verze 2.0, nepoužívejte `StepOut` s STOP_UNMANAGED nastaven příznak vzhledem k tomu, že se nezdaří. (Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) nastavit pro krokování s příznaky.) Spolupráce ladicí programy musí krok do nativního kódu sami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
