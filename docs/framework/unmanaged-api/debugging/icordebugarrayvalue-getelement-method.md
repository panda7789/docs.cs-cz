---
title: "ICorDebugArrayValue::GetElement – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElement
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aba987aa6f806bfe1608e081aac4cb501cd23fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement – metoda
Získá hodnotu pro dané pole elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdim`  
 [v] Počet dimenzí tohoto `ICorDebugArrayValue` objektu.  
  
 Tato hodnota je také velikost `indices` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.  
  
 `indices`  
 [v] Pole hodnot index, z nichž každý určuje pozici v rámci dimenze `ICorDebugArrayValue` objektu.  
  
 Tato hodnota nesmí být null.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu zadaného prvku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
