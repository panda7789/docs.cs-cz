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
ms.openlocfilehash: 25cd3e05bc80dd39d2ca558bb4dd5fb77d255f5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791398"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames – metoda
Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.  
  
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
|S_OK|Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.|  
|E_INVALIDARG|`cInternalFrames` není nula a `ppInternalFrames` je `null`nebo `pcInternalFrames` `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` je menší než počet vnitřních snímků.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.  
  
 Při prvním volání `GetActiveInternalFrames`byste měli nastavit parametr `cInternalFrames` na hodnotu 0 (nula) a parametr `ppInternalFrames` na hodnotu null. Když `GetActiveInternalFrames` první vrátí, `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.  
  
 `GetActiveInternalFrames` by se měla volat podruhé. V parametru `cInternalFrames` byste měli předat správný počet (`pcInternalFrames`) a určit ukazatel na pole odpovídající velikosti v `ppInternalFrames`.  
  
 K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
