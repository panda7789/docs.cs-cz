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
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976262"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult – metoda
Získá výsledky tohoto vyhodnocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppResult`  
 mimo Ukazatel na adresu objektu ICorDebugValue, který představuje výsledky tohoto vyhodnocení, pokud se vyhodnocení dokončí normálně.  
  
## <a name="remarks"></a>Poznámky  
 `GetResult` Metoda je platná až po dokončení vyhodnocení.  
  
 Pokud se vyhodnocení dokončí normálně `ppResult` , zadává výsledky. Pokud se ukončí s výjimkou, výsledek je vyvolána výjimka. Pokud bylo vyhodnocení nového objektu, výsledkem je odkaz na nový objekt.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
