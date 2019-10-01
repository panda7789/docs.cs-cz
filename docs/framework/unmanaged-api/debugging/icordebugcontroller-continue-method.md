---
title: ICorDebugController::Continue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf59ee3c7bf41a2bb0ff68db5e70dd5a519a0e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700785"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue – metoda

Pokračuje v provádění spravovaných vláken po volání [metody Stop](icordebugcontroller-stop-method.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>Parametry

 `fIsOutOfBand`  
 pro Nastavte na `true`, pokud budete pokračovat v události mimo IP síť. v opačném případě nastavte na `false`.

## <a name="remarks"></a>Poznámky

`Continue` pokračuje v procesu po volání metody `ICorDebugController::Stop`.

Při ladění v kombinovaném režimu Nevolejte `Continue` ve vlákně události Win32, pokud nebudete pokračovat z události mimo IP síť.

Integrovaná *událost* je buď spravovaná událost, nebo normální nespravovanou událost, během které ladicí program podporuje interakci se spravovaným stavem procesu. V tomto případě ladicí program obdrží zpětné volání [ICorDebugUnmanagedCallback –::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) s parametrem `fOutOfBand` nastaveným na `false`.
  
*Událost mimo pásmo* je nespravovaná událost, během které je interakce se spravovaným stavem procesu neproveditelná v době, kdy se proces zastavil kvůli události. V tomto případě ladicí program obdrží zpětné volání `ICorDebugUnmanagedCallback::DebugEvent` s parametrem `fOutOfBand` nastaveným na `true`.

## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Hlavička:** CorDebug. idl, CorDebug. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
