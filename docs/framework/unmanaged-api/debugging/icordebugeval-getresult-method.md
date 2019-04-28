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
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667116"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult – metoda
Získá výsledky vyhodnocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
