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
ms.openlocfilehash: b4f228d55c9ffd6b85ebd0b430a7f5db404320f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124337"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames – metoda
Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) v zásobníku.  
  
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
 pro Počet vnitřních snímků očekávaných v `ppInternalFrames`.  
  
 `pcInternalFrames`  
 mimo Ukazatel na `ULONG32`, který obsahuje počet vnitřních snímků v zásobníku.  
  
 `ppInternalFrames`  
 [in, out] Ukazatel na adresu pole vnitřních snímků v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Objekt [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) byl úspěšně vytvořen.|  
|E_INVALIDARG|`cInternalFrames` není nula a `ppInternalFrames` je `null`nebo `pcInternalFrames` `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` je menší než počet vnitřních snímků.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.  
  
 Při prvním volání `GetActiveInternalFrames`byste měli nastavit parametr `cInternalFrames` na hodnotu 0 (nula) a parametr `ppInternalFrames` na hodnotu null. Když `GetActiveInternalFrames` první vrátí, `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.  
  
 `GetActiveInternalFrames` by se měla volat podruhé. V parametru `cInternalFrames` byste měli předat správný počet (`pcInternalFrames`) a určit ukazatel na pole odpovídající velikosti v `ppInternalFrames`.  
  
 K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
