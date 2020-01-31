---
title: ICorDebugNativeFrame2::IsMatchingParentFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aeaa706ef35413a728f8b254cd325f0bcc83acd1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792716"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame – metoda
Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>Parametry  
 `pPotentialParentFrame`  
 pro Ukazatel na objekt rámce, který chcete vyhodnotit pro nadřazený stav.  
  
 `pIsParent`  
 [out] `true`, pokud je `pPotentialParentFrame` nadřazená aktuálnímu snímku; v opačném případě `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Nadřazený stav byl úspěšně vrácen.|  
|E_FAIL|Nadřazený stav nelze vrátit.|  
|E_INVALIDARG|`pPotentialParentFrame` nebo `pIsParent` je null.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `IsMatchingParentFrame` vrátí `true`, pokud je objekt Frame, který předáte metodě, nadřazený objektu rámce, na kterém byla metoda volána. Pokud voláte metodu na rámec, který není podřízenou položkou zadaného rámce, vrátí chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugNativeFrame2 – rozhraní](icordebugnativeframe2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
