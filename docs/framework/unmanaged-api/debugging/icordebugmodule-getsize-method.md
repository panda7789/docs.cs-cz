---
title: "ICorDebugModule::GetSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9474b48526e2ba6292c28e5e66eb97f8e57f2a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetsize-method"></a>ICorDebugModule::GetSize – metoda
Získá velikost v bajtech modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcBytes`  
 [out] Velikost modulu v bajtech.  
  
 Pokud v modulu bylo vytvořeno ze Generátor nativních bitových kopií (NGen.exe), bude velikost modulu nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
