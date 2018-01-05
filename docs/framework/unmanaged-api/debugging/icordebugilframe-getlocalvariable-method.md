---
title: "ICorDebugILFrame::GetLocalVariable – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetLocalVariable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9694ee2e27d8789b661abc7393a480411c2b0191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetlocalvariable-method"></a>ICorDebugILFrame::GetLocalVariable – metoda
Získá hodnotu zadaného místní proměnné v rámci zásobníku tento Microsoft (MSIL intermediate language).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 [v] Index místní proměnné v rámci této MSIL zásobníku.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který reprezentuje načtené hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalVariable` Metodu lze použít rámce zásobníku MSIL nebo v rámci kompilované v běhu (JIT).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
