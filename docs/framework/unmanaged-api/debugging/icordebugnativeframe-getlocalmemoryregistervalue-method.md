---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 788ce2d47769caa72518e0357a0affdff5862699
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137288"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnné, z nichž jsou v zadaném registru a umístění paměti pro tento nativní rámec uloženy malá slova a velká slova v uvedeném pořadí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `highWordAddress`  
 pro Hodnota `CORDB_ADDRESS`, která určuje umístění paměti obsahující vysoké slovo hodnoty.  
  
 `lowWordRegister`  
 pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující nedostatečné slovo hodnoty.  
  
 `cbSigBlob`  
 pro Celé číslo, které určuje velikost binárního podpisu metadat, na které odkazuje parametr `pvSigBlob`.  
  
 `pvSigBlob`  
 pro Hodnota `PCCOR_SIGNATURE`, která odkazuje na binární signaturu metadat typu hodnoty.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru a umístění v paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
