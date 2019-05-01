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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a25e52c6b858aaa602ffade0e407b1aaf6e5c67e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995582"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP – metoda
Nastaví ukazatele na instrukci do zadaného umístění posunu v kódu Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 Umístění posunu v kódu MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Volání `SetIP` okamžitě zneplatnit všechny rámce a řetězce pro aktuální vlákno. Pokud ladicí program potřebuje informace o snímcích po volání `SetIP`, je nutné provést nové trasování zásobníku.  
  
 [Icordebug –](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu. Ale i v případě, že rámec je příkaz v platném stavu, stále může existovat problémy, jako je neinicializovaných místních proměnných. Volající zodpovídá za to integrita spuštěný program.  
  
 Na 64bitových platformách, ukazatele na instrukci nelze přesunout z celkového počtu `catch` nebo `finally` bloku. Pokud `SetIP` nazývá provést přesun na 64bitové platformě, vrátí HRESULT označující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
