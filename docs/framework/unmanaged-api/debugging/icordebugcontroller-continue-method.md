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
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892855"
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
pro Nastavte na `true` , pokud budete pokračovat v události mimo IP síť. v opačném případě `false`nastavte na.

## <a name="remarks"></a>Poznámky

`Continue`pokračuje v procesu po volání `ICorDebugController::Stop` metody.

Při ladění v kombinovaném režimu Nevolejte `Continue` do vlákna události Win32, pokud nebudete pokračovat z události mimo IP síť.

Integrovaná *událost* je buď spravovaná událost, nebo normální nespravovanou událost, během které ladicí program podporuje interakci se spravovaným stavem procesu. V tomto případě ladicí program obdrží zpětné volání [ICorDebugUnmanagedCallback –::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) s jeho `fOutOfBand` parametrem nastaveným `false`na.

*Událost mimo pásmo* je nespravovaná událost, během které je interakce se spravovaným stavem procesu neproveditelná v době, kdy se proces zastavil kvůli události. V tomto případě ladicí program obdrží `ICorDebugUnmanagedCallback::DebugEvent` zpětné volání s `fOutOfBand` parametrem nastaveným na `true`.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
