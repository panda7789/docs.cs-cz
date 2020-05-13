---
title: ICorDebugILFrame::SetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 325b2a009e77d87e95bdb02803dd3c4675c26ddc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213423"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP – metoda
Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 Umístění posunu v kódu jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno. Pokud ladicí program potřebuje informace o snímku po volání `SetIP` , musí provést nové trasování zásobníku.  
  
 [ICorDebug](icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu. Nicméně i v případě, že je rámec v platném stavu, mohou být stále problémy, jako například neinicializované místní proměnné. Volající je zodpovědný za zajištění návaznosti běžícího programu.  
  
 Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` bloku nebo `finally` . Pokud `SetIP` je volána k provedení takového přesunu na 64 platformě, vrátí HRESULT indikující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
