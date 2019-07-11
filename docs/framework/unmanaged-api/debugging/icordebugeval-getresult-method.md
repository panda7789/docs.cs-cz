---
title: ICorDebugEval::GetResult – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752937"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult – metoda
Získá výsledky vyhodnocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppResult`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje výsledky hodnocení, pokud se obvykle dokončí hodnocení.  
  
## <a name="remarks"></a>Poznámky  
 `GetResult` Metoda je platná, až po dokončení hodnocení.  
  
 Pokud se hodnocení dokončí za normálních okolností `ppResult` určuje výsledky. Pokud je ukončena výjimku, výsledkem je výjimka vyvolána. Pokud je hodnocení pro nový objekt, výsledkem je odkaz na nový objekt.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
