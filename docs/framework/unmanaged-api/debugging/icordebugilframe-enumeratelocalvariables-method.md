---
title: "ICorDebugILFrame::EnumerateLocalVariables – metoda"
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
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables – metoda
Získá enumerátor pro místní proměnné do tohoto rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 [out] Ukazatel na adresu ICorDebugValueEnum objekt, který je enumerátor pro místní proměnné do tohoto rámce.  
  
## <a name="remarks"></a>Poznámky  
 `EnumerateLocalVariables`Získá enumerátor, který může být uveden lokální proměnné, které jsou k dispozici v rámci volání, která je reprezentována tento objekt ICorDebugILFrame. V seznamu nemusí zahrnovat všechny lokální proměnné ve funkci spuštěné, protože některé z nich nemusí být aktivní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
