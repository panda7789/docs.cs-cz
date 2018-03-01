---
title: "ICorDebugChain::EnumerateFrames – metoda"
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
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames – metoda
Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaných v řetězu, počínaje nejnovější rámečku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppFrames`  
 [out] Ukazatel na adresu ICorDebugFrameEnum objekt, který je enumerátor pro rámce zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Řetězu představuje zásobníku volání fyzické pro vlákno.  
  
 `EnumerateFrames` Metoda by měla být volána pouze pro spravované řetězy. Rozhraní API pro ladění neposkytuje metody pro získání snímky obsažené v nespravované řetězy. Ladicí program musí získat tyto informace používat jiným způsobem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
