---
title: ICorDebugNativeFrame2::GetStackParameterSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: b88b3907eb555050de93f35411629b2bd30c7375
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212942"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a>ICorDebugNativeFrame2::GetStackParameterSize – metoda
Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a>Parametry  
 `pSize`  
 mimo Ukazatel na kumulativní velikost parametrů v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Velikost zásobníku byla úspěšně vrácena.|  
|S_FALSE|`GetStackParameterSize`byla volána na platformě, která není x86.|  
|E_FAIL|`The size of the parameters could not be returned`.|  
|E_INVALIDARG|`pSize`Je `null` .|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Metody [ICorDebugStackWalk](icordebugstackwalk-interface.md) neupravují ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku. Místo toho můžete použít hodnotu vrácenou `GetStackParameterSize` pro úpravu ukazatele zásobníku na osazení nativního unwindu, který je upraven pro parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugNativeFrame2 – rozhraní](icordebugnativeframe2-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
