---
title: "ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ece07fcffbc0d0e6b8cf06cc04866c1b651e6a01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
Získá hodnotu argumentu nebo místní proměnné, která je uložená v dvě zaregistruje zadaný pro tento nativní rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `highWordReg`  
 [v] Hodnota výčtu "CorDebugRegister", který určuje registrace obsahující slovo vysoké hodnoty.  
  
 `lowWordReg`  
 [v] Hodnota `CorDebugRegister` výčet, který určuje registru obsahujícího nízkou slovo hodnoty.  
  
 `cbSigBlob`  
 [v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.  
  
 `pvSigBlob`  
 [v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty uložené v zadané Registry.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalDoubleRegisterValue` Metodu lze použít buď v nativní rámce nebo v běhu (JIT)-zkompilovat rámce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
