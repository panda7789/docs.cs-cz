---
title: ICorDebugCode::CreateBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint – metoda
Vytvoří zarážky v tomto segmentu kódu na zadaném posunu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [v] Posun, pro kterou chcete vytvořit bod přerušení.  
  
 `ppBreakpoint`  
 [out] Ukazatel na adresu "ICorDebugFunctionBreakpoint" objekt, který představuje bod přerušení.  
  
## <a name="remarks"></a>Poznámky  
 Předtím, než je aktivní bod přerušení, musí být přidané na objekt procesu.  
  
 Pokud tento kód je kód Microsoft intermediate language (MSIL), a dojde v běhu (JIT)-kompilované, nativní verzi kód zarážce se použijí v kompilována kódu. (Stejná je hodnota true, pokud kód je kompilována později.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
