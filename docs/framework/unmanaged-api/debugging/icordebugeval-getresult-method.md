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
ms.openlocfilehash: 7e160eddf667b542929c8dd3790de666a8e8bb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413056"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult – metoda
Získá výsledky tohoto hodnocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppResult`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje výsledky tohoto hodnocení, pokud vyhodnocení dokončení normálně.  
  
## <a name="remarks"></a>Poznámky  
 `GetResult` Metoda je platná pouze po dokončení vyhodnocení.  
  
 Za normálních okolností dokončení vyhodnocení `ppResult` určuje výsledky. Pokud ho ukončí s výjimkou, výsledkem je, že došlo k výjimce. Pokud pro nový objekt, který byl vyhodnocení, výsledkem je odkaz na nový objekt.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
