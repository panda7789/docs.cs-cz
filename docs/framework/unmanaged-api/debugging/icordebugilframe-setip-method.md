---
title: "ICorDebugILFrame::SetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP – metoda
Nastaví ukazatel instrukce do zadaného umístění posunu v kódu (MSIL intermediate language) společnosti Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOffset`  
 Umístění posunu v MSIL kódu.  
  
## <a name="remarks"></a>Poznámky  
 Volání `SetIP` okamžitě zneplatní všechny snímky a řetězy pro aktuální vlákno. Pokud ladicí program musí rámce informace po volání `SetIP`, je třeba provést nové trasování zásobníku.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu. Ale i pokud rámečku není v platném stavu, stále může mít problémy, třeba neinicializovaných místních proměnných. Volající zodpovídá za zajištění integrita spuštěného programu.  
  
 Na 64bitových platformách, nelze jej přesunout ukazatel instrukce mimo `catch` nebo `finally` bloku. Pokud `SetIP` nazývá aby přesunu na 64bitové platformě, vrátí HRESULT udávající neúspěch.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
