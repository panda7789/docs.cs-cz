---
title: ICorDebugChain::GetThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291c8129a790c235ee6e7f163c49c4e1e726cce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetthread-method"></a>ICorDebugChain::GetThread – metoda
Získá fyzické vlákno, které je tento řetězec volání součástí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Ukazatel na ICorDebugThread objekt, který reprezentuje fyzický vlákno této řetěz volání je součástí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
