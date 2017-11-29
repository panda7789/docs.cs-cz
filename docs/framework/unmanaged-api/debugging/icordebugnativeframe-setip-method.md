---
title: "ICorDebugNativeFrame::SetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 563566a877d589ecd32575c095cdc812c28f6334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP – metoda
Nastaví ukazatel instrukce do zadaného umístění posunu v nativním kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOffset`  
 [v] Umístění posunu v nativním kódu.  
  
## <a name="remarks"></a>Poznámky  
 Volání `SetIP` okamžitě zneplatní všechny snímky a řetězy pro aktuální vlákno. Pokud ladicí program musí rámce informace po volání `SetIP`, je třeba provést nové trasování zásobníku.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu. Ale i pokud rámečku není v platném stavu, co se týče modulu runtime, stále může mít problémy, jako je například neinicializovaných místních proměnných a tak dále. Volající zodpovídá za pojištění integrita spuštěného programu.  
  
 Na 64bitových platformách, nelze jej přesunout ukazatel instrukce mimo `catch` nebo `finally` bloku. Pokud `SetIP` nazývá aby přesunu na 64bitové platformě, vrátí HRESULT udávající neúspěch.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
