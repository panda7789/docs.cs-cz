---
title: "ICorDebugDataTarget::GetPlatform – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetPlatform Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c19e472ef571def1011d2a00701fea3a6fadfea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform – metoda
Poskytuje informace o platformě, včetně architekturu procesoru a operačního systému, na kterém je tento cílový proces běží.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 [out] Ukazatel [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) výčet, který popisuje cílové platformy.  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugPlatformEnum` Návratová hodnota výčtu je používán [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní zjistěte informace o procesu cíl například velikost ukazatele, rozložení prostoru adres, registrace sady, formát instrukce, kontext rozložení a konvence volání.  
  
 `pTargetPlatform` Hodnotu mohou odkazovat na platformu, která je emulovaných pro cílové místo zadání skutečné hardwarové používán. Například by měl použít procesu, který je spuštěn v systému Windows v prostředí systému Windows (WOW) v 64bitové edici operačního systému Windows `CORDB_PLATFORM_WINDOWS_X86` hodnotu [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) výčtu.  
  
 Tato metoda musí být úspěšné. Pokud se nezdaří, nepoužitelná cílové platformy. Metoda může selhat z následujících důvodů:  
  
-   Platforma, která je emulovaných pro cíl nepoužitelný.  
  
-   Skutečné hardwarové na cílové platformy nepoužitelný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
