---
title: ICorDebugStackWalk::GetFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 89576e2b3d5fb4df0cccfdd28c80a5cb67331597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791889"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame – metoda
Načte aktuální rámec v objektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrame`  
 pro Ukazatel na adresu vytvořeného objektu Frame, který představuje aktuální rámec v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Modul runtime úspěšně vrátil aktuální rámec.|  
|E_FAIL|Aktuální rámec nebyl vrácen.|  
|S_FALSE|Aktuální rámec je nativní rámec zásobníku.|  
|E_INVALIDARG|`pFrame` je null.|  
|CORDBG_E_PAST_END_OF_STACK|Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStackWalk` vrátí pouze skutečné rámce zásobníku. K vrácení vnitřních rámců použijte metodu [ICorDebugThread3:: GetActiveInternalFrames –](icordebugthread3-getactiveinternalframes-method.md) . (Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugStackWalk – rozhraní](icordebugstackwalk-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
