---
title: ICorDebugNativeFrame::SetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096743"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP – metoda
Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 pro Umístění posunu v nativním kódu.  
  
## <a name="remarks"></a>Poznámky  
 Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno. Pokud ladicí program potřebuje informace o snímku po volání `SetIP`, musí provést nové trasování zásobníku.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu. Nicméně i v případě, že je rámec v platném stavu, je-li daný modul runtime, stále se může jednat o problémy, jako například neinicializované místní proměnné a tak dále. Volající je zodpovědný za pojištění soudržnosti běžícího programu.  
  
 Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` nebo `finally` bloku. Pokud je volána `SetIP` k provedení tohoto přesunu na 64 platformě, vrátí HRESULT indikující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
