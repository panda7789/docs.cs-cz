---
title: ICorDebugReferenceValue::SetValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f0c06f9b04c5f15171464b93dc93765625d6f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevaluesetvalue-method"></a>ICorDebugReferenceValue::SetValue – metoda
Nastaví adresu zadanou paměti. To znamená tato metoda nastaví tento ICorDebugReferenceValue tak, aby odkazoval na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 [v] A `CORDB_ADDRESS` hodnotu, která určuje adresu objektu, ke kterému tato `ICorDebugReferenceValue` body.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
