---
title: ICorDebugNativeFrame::GetLocalRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f53c8290271391e52176f8364b592ce6b46faf71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195940"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnná, která je uložena do zadaného registru pro tuto nativní rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `reg`  
 [in] Hodnota výčtu "cordebugregister –", který určuje do registru, který obsahuje hodnotu.  
  
 `cbSigBlob`  
 [in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt představující získanou hodnotu, která je uložena do zadaného registru.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalRegisterValue` Metodu je možné použít ve službě je nativní rámec nebo just-in-time (JIT)-zkompilován rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
