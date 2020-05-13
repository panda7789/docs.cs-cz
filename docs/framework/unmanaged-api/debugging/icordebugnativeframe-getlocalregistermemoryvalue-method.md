---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213293"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda
Získá hodnotu argumentu nebo místní proměnné, z nichž je pro tento nativní rámec uloženo méně slov a vysoké slovo v umístění paměti a určeném registru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `highWordReg`  
 pro Hodnota výčtu "CorDebugRegister –", která určuje registr obsahující vysoké slovo hodnoty.  
  
 `lowWordAddress`  
 pro `CORDB_ADDRESS`Hodnota, která určuje umístění paměti obsahující nedostatečné slovo hodnoty.  
  
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
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také
