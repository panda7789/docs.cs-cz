---
title: ICorDebugCode::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 949cf322be4b7981a8c569f24abd1d9e29fa5ae6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973142"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping – metoda
Získává pole instancí "cor_debug_il_to_native_map –", které představují mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMap`  
 [in] Velikost `map` pole.  
  
 `pcMap`  
 [out] Ukazatel na skutečný počet prvků vrácených v `map` pole.  
  
 `map`  
 [out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý představuje mapování z jazyka MSIL posun na nativní posun.  
  
 Neexistuje žádné řazení k poli prvků vrácených.  
  
## <a name="remarks"></a>Poznámky  
 `GetILToNativeMapping` Metoda vrátí smysluplné výsledky, pouze v případě, že tato instance "ICorDebugCode" představuje nativní kód, který byl just-in-time (JIT) kompilaci kódu jazyka MSIL.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Icordebugcode – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
