---
title: "ICorDebugController::Stop – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a8699a54814b37cc03404b72330812f3eb2b2f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop – metoda
Provede spolupráci zastavení všech vláken, které jsou spuštěny spravovaného kódu v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nepoužívá se.  
  
## <a name="remarks"></a>Poznámky  
 `Stop`provede spolupráci zastavení na všechna vlákna systémem spravované kódu v procesu. Během ladicí relace pouze pro spravované, nespravované vláken nadále spustit (ale zablokuje při pokusu o volání spravovaný kód). Během zprostředkovatel komunikace s objekty ladicí relace bude také zastavena nespravovaná vlákna. `dwTimeoutIgnored` Hodnota je aktuálně ignorován a považován za NEKONEČNÉ (-1). Pokud spolupráci zastavení nezdaří z důvodu zablokování, jsou pozastavena všechna vlákna a je vrácen E_TIMEOUT.  
  
> [!NOTE]
>  `Stop`je pouze synchronní metoda v rozhraní API pro ladění. Když `Stop` vrátí S_OK, proces se zastaví. Bez zpětného volání dostane oznámení naslouchací procesy tabulátoru. Ladicí program musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) povolit pokračování procesu.  
  
 Ladicí program udržuje čítač zastavit. Pokud čítač přejde na hodnotu nula, je obnoven běh kontroleru. Každé volání `Stop` nebo každý odeslat zpětné volání zvýší čítače. Každé volání `ICorDebugController::Continue` snížení hodnoty čítače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
