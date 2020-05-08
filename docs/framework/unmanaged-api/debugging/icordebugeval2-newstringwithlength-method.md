---
title: ICorDebugEval2::NewStringWithLength – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976067"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength – metoda
Vytvoří řetězec o zadané délce se zadaným obsahem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `string`  
 pro Ukazatel na hodnotu řetězce.  
  
 `uiLength`  
 pro Délka řetězce  
  
## <a name="remarks"></a>Poznámky  
 Pokud se očekává, že je koncový znak null řetězce ve spravovaném řetězci, volající `NewStringWithLength` metody musí zajistit, aby délka řetězce zahrnovala koncový znak null.  
  
 Řetězec je vždy vytvořen v doméně aplikace, ve které je vlákno aktuálně prováděno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
