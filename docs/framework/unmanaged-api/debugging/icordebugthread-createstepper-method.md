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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 626f313c41c85e08901648f429d99c829ba35e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper – metoda
Vytvoří objekt ICorDebugStepper, který umožňuje procházení aktivní rámec této ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppStepper`  
 [out] Ukazatel na adresu `ICorDebugStepper` objekt, který umožňuje procházení aktivní rámec tohoto podprocesu.  
  
## <a name="remarks"></a>Poznámky  
 Nespravovaný kód může být aktivní rámec.  
  
 `ICorDebugStepper` Rozhraní musí lze použít k provedení skutečné krokování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
