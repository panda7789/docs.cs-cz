---
title: "ICorDebugThread3::GetActiveInternalFrames – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ecfbaeff9416ee8e6541a23bac6ec76f99abd2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames – metoda
Vrátí pole interní rámce ([icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objekty) v zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cInternalFrames`  
 [v] Počet interní rámce v očekává `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Ukazatel na `ULONG32` obsahující počet interní rámce v zásobníku.  
  
 `ppInternalFrames`  
 [ve out] Ukazatel na adresu pole interní rámce v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|[Icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objekt byl úspěšně vytvořen.|  
|E_INVALIDARG|`cInternalFrames`není nula a `ppInternalFrames` je `null`, nebo `pcInternalFrames` je `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`je menší než počet interní rámce.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Interní rámce jsou vloženy do zásobníku modulem runtime pro uložení dočasných dat datové struktury.  
  
 Při prvním volání `GetActiveInternalFrames`, byste měli nastavit `cInternalFrames` parametru na hodnotu 0 (nula) a `ppInternalFrames` parametr na hodnotu null. Když `GetActiveInternalFrames` nejprve vrátí, `pcInternalFrames` obsahuje počet interní rámce v zásobníku.  
  
 `GetActiveInternalFrames`by pak volat ještě jednou. By měla předávat správný počet (`pcInternalFrames`) v `cInternalFrames` parametr, a zadejte ukazatel na odpovídajícím způsobem velikosti pole v `ppInternalFrames`.  
  
 Použití [icordebugstackwalk::getframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí skutečné zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
