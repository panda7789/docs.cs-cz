---
title: ICorDebugInternalFrame2::IsCloserToLeaf – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 4a01ccd4e5cb9aadc6a693b2c6ceaff31c114bbc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209887"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf – metoda
Kontroluje, zda `this` je interní rámec blíže k listu, než je zadaný objekt ICorDebugFrame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrameToCompare`  
 pro Ukazatel na `ICorDebugFrame` objekt porovnání.  
  
 `pIsCloser`  
 [out] `true` Pokud `this` interní rámec je blíž k listu, než je rámec určený v `pFrameToCompare` ; v opačném případě `false` .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Porovnání bylo úspěšně provedeno.|  
|E_FAIL|Porovnání nelze provést.|  
|E_INVALIDARG|`pFrameToCompare`nebo `pIsCloser` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 `IsCloserToLeaf`dá se použít k implementaci zásady pro překládání vnitřních snímků s ostatními snímky v zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugInternalFrame2 – rozhraní](icordebuginternalframe2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
