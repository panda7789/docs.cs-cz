---
title: ICorDebugThread3::GetActiveInternalFrames – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178469"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames – metoda
Vrátí pole vnitřních rámců ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objekty) v zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>Parametry  
 `cInternalFrames`  
 [v] Počet interních rámců `ppInternalFrames`očekávaných v .  
  
 `pcInternalFrames`  
 [out] Ukazatel na `ULONG32` a, který obsahuje počet vnitřních rámců v zásobníku.  
  
 `ppInternalFrames`  
 [dovnitř, ven] Ukazatel na adresu pole vnitřních rámců v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULTs, stejně jako HRESULT chyby, které označují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.|  
|E_invalidarg|`cInternalFrames`není nula `ppInternalFrames` `null`a `pcInternalFrames` je `null`, nebo je .|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`je menší než počet vnitřních rámců.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Vnitřní rámce jsou datové struktury posunuté do zásobníku za běhu pro ukládání dočasných dat.  
  
 Při prvním `GetActiveInternalFrames`volání byste měli `cInternalFrames` nastavit parametr na 0 `ppInternalFrames` (nula) a parametr na hodnotu null. Při `GetActiveInternalFrames` prvním `pcInternalFrames` vrátí, obsahuje počet vnitřních rámců v zásobníku.  
  
 `GetActiveInternalFrames`by pak měl být volán podruhé. Měli byste předat správný`pcInternalFrames`počet `cInternalFrames` ( ) v parametru a určit ukazatel `ppInternalFrames`na vhodně velké pole v .  
  
 Použijte metodu [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) k vrácení skutečných rámců zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [ladění](index.md)
