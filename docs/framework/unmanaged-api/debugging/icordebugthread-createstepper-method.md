---
title: ICorDebugThread::CreateStepper – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133594"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper – metoda
Vytvoří objekt ICorDebugStepper, který umožňuje krokování skrze aktivní rámec tohoto ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppStepper`  
 mimo Ukazatel na adresu `ICorDebugStepper` objektu, který umožňuje krokování skrze aktivní rámec tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 Aktivní rámec může být nespravovaný kód.  
  
 K provedení samotného krokování je nutné použít rozhraní `ICorDebugStepper`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
