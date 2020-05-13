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
ms.openlocfilehash: 5bcced647af6436bd8f5b1f3779d9368b6173d11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213033"
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
 [out] `true` Pokud `pPotentialParentFrame` je nadřazená aktuální rámec, v opačném případě `false` .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Nadřazený stav byl úspěšně vrácen.|  
|E_FAIL|Nadřazený stav nelze vrátit.|  
|E_INVALIDARG|`pPotentialParentFrame`nebo `pIsParent` má hodnotu null.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `IsMatchingParentFrame`Vrátí, `true` zda je objekt Frame, který předáte metodě, nadřazený objektu rámce, na kterém byla metoda volána. Pokud voláte metodu na rámec, který není podřízenou položkou zadaného rámce, vrátí chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugNativeFrame2 – rozhraní](icordebugnativeframe2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
