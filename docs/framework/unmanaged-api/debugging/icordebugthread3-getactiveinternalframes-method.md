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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379854"
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
 pro Počet vnitřních rámců očekávaných v `ppInternalFrames` .  
  
 `pcInternalFrames`  
 mimo Ukazatel na `ULONG32` , který obsahuje počet vnitřních snímků v zásobníku.  
  
 `ppInternalFrames`  
 [in, out] Ukazatel na adresu pole vnitřních snímků v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.|  
|E_INVALIDARG|`cInternalFrames`není nula a `ppInternalFrames` je `null` nebo `pcInternalFrames` `null` .|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`je menší než počet vnitřních snímků.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.  
  
 Při prvním volání `GetActiveInternalFrames` byste měli nastavit `cInternalFrames` parametr na hodnotu 0 (nula) a `ppInternalFrames` parametr na hodnotu null. Při `GetActiveInternalFrames` prvním návratu `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.  
  
 `GetActiveInternalFrames`by se pak mělo volat podruhé. V parametru byste měli předat správný počet ( `pcInternalFrames` ) `cInternalFrames` a zadat ukazatel na pole odpovídající velikosti v `ppInternalFrames` .  
  
 K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
