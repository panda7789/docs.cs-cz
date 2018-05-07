---
title: ICorDebugReferenceValue::IsNull – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c82c72350931bf3aed8ec6699cd0af834798e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull – metoda
Získá hodnotu, která určuje, zda tento ICorDebugReferenceValue v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbNull`  
 [out] Ukazatel na logickou hodnotu, která je `true` Pokud `ICorDebugReferenceValue` objekt je null; jinak hodnota `pbNull` je `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
