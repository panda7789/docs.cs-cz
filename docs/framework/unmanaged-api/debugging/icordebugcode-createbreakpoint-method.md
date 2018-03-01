---
title: "ICorDebugCode::CreateBreakpoint – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
