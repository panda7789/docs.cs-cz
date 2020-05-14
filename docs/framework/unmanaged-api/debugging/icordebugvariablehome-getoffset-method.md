---
title: 'ICorDebugVariableHome:: GetOffset – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 75a165e2fd517f36d779a934a5bdd9c41956411a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396766"
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome:: GetOffset – metoda
Získá posun od základního registru pro proměnnou.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pOffset`  
 mimo Posun základního registru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací následující hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Proměnná je v umístění relativní paměti pro registraci.|  
|`E_FAIL`|Proměnná není v umístění relativní paměti registru.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
