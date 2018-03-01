---
title: "ICorDebugNativeFrame::GetLocalRegisterValue – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03f528547797cd7eaf7d18ba63203bcbf0300e69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnné, které jsou uloženy v zadané registrace pro tento nativní rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reg`  
 [v] Hodnota výčtu "CorDebugRegister", který určuje registrace, který obsahuje hodnotu.  
  
 `cbSigBlob`  
 [v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.  
  
 `pvSigBlob`  
 [v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty uložené v zadané registrace.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalRegisterValue` Metodu lze použít buď v nativní rámce nebo v běhu (JIT)-zkompilovat rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
