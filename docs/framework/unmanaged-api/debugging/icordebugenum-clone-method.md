---
title: "ICorDebugEnum::Clone – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum.Clone
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ddd7d82b6eb2944b1d2a5d7a83f0ccc9f255e45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumclone-method"></a>ICorDebugEnum::Clone – metoda
Vytvoří kopii tohoto objektu ICorDebugEnum.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel na adresu `ICorDebugEnum` objekt, který je kopií této `ICorDebugEnum` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
