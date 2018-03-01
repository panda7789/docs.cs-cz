---
title: "ICorDebugILFrame::EnumerateArguments – metoda"
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
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a>ICorDebugILFrame::EnumerateArguments – metoda
Získá enumerátor pro argumenty do tohoto rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 [out] Ukazatel na adresu ICorDebugValueEnum objekt, který je enumerátor pro argumenty do tohoto rámce.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateArguments`Získá enumerátor, který můžete zobrazit seznam argumentů, které jsou k dispozici v rámci volání, která je reprezentována tento objekt ICorDebugILFrame. Obsahuje seznam argumentů, které jsou [vararg](/cpp/windows/vararg) (tedy proměnný počet argumentů) a také argumenty, které nejsou `vararg`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
