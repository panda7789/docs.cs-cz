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
ms.openlocfilehash: 91f0a75f127afcff89c2b92bf3ed67466b205081
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213046"
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
 pro `CORDB_ADDRESS`Hodnota, která určuje umístění paměti obsahující vysoké slovo hodnoty.  
  
 `lowWordRegister`  
 pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující nedostatečné slovo hodnoty.  
  
 `cbSigBlob`  
 pro Celé číslo, které určuje velikost binárního podpisu metadat, na který odkazuje `pvSigBlob` parametr.  
  
 `pvSigBlob`  
 pro `PCCOR_SIGNATURE`Hodnota, která odkazuje na binární signaturu metadat typu hodnoty.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném registru a umístění v paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
