---
title: "ICorDebugAppDomain::EnumerateSteppers – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateSteppers
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b410eabee546307488449e577d9e102ac6a210b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a>ICorDebugAppDomain::EnumerateSteppers – metoda
Získá enumerátor pro všechny aktivní steppers v doméně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppSteppers`  
 [out] Ukazatel na adresu ICorDebugStepperEnum objekt, který je enumerátor pro všechny aktivní steppers v doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
