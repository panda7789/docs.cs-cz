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
ms.openlocfilehash: 5dd93dcc29ace6573e313f732c45af0dfbb900e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782216"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf – metoda
Kontroluje, zda je vnitřní rámec `this` blíž k listu, než je zadaný objekt ICorDebugFrame.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrameToCompare`  
 pro Ukazatel na objekt porovnání `ICorDebugFrame`.  
  
 `pIsCloser`  
 [out] `true`, zda `this` interní rámec je blíž k listu, než je rámec určený `pFrameToCompare`; v opačném případě `false`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Porovnání bylo úspěšně provedeno.|  
|E_FAIL|Porovnání nelze provést.|  
|E_INVALIDARG|`pFrameToCompare` nebo `pIsCloser` je null.|  
  
## <a name="remarks"></a>Poznámky  
 `IsCloserToLeaf` lze použít k implementaci zásad pro překládání vnitřních snímků s ostatními snímky v zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugInternalFrame2 – rozhraní](icordebuginternalframe2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
