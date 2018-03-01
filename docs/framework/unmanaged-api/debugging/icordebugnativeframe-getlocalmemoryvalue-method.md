---
title: "ICorDebugNativeFrame::GetLocalMemoryValue – metoda"
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
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ca48d10f4701064c69d397a224f0c87574be58a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryValue – metoda
Získá hodnotu argumentu nebo místní proměnné, která je uložena v umístění zadaná paměťová tato nativní rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] A `CORDB_ADDRESS` hodnotu, která určuje umístění v paměti, který obsahuje hodnotu.  
  
 `cbSigBlob`  
 [v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.  
  
 `pvSigBlob`  
 [v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty, který je uložen v umístění zadaná paměťová.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
