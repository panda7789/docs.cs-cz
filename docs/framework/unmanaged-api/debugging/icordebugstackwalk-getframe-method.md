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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89515ab0ff08eadfb1eafdf70ead0bc1e0a17628
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487723"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame – metoda
Získá aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrame`  
 [in] Ukazatel na adresu vytvořeného orámovat objekt, který představuje aktuální rámec v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Modul runtime byla úspěšně vrácena aktuální rámec.|  
|E_FAIL|Aktuální rámec nebyl vrácen.|  
|S_FALSE|Aktuální rámec je příkaz nativní zásobníku.|  
|E_INVALIDARG|`pFrame` má hodnotu null.|  
|CORDBG_E_PAST_END_OF_STACK|Už na konec zásobníku; ukazatel na rámec Proto je možný žádné další rámce.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugStackWalk` Vrátí pouze skutečné rámců. Použití [icordebugthread3::getactiveinternalframes –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí interní snímků. (Vnitřních rámcích datové struktury jsou vloženy do zásobníku modulem runtime k uložení dočasných dat..)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugStackWalk – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
