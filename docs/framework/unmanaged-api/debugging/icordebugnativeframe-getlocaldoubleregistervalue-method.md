---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 21c4d00e4156b9db27ae4188aace19764a2be53e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213072"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnné, která je uložena ve dvou zadaných registrech pro tento nativní rámec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `highWordReg`  
 pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující vysoké slovo hodnoty.  
  
 `lowWordReg`  
 pro Hodnota `CorDebugRegister` výčtu, která určuje registr obsahující nedostatečné slovo hodnoty.  
  
 `cbSigBlob`  
 pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.  
  
 `pvSigBlob`  
 pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaných registrech.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalDoubleRegisterValue`Metodu lze použít buď v nativním rámci, nebo v rámci zkompilovaného snímku JIT (just-in-time).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
