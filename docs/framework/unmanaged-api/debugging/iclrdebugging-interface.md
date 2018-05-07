---
title: ICLRDebugging – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b7fa5e61ba6f967544d8ebeee2f1c6a8d3a7b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging – rozhraní
Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OpenVirtualProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|Získá rozhraní "ICorDebugProcess", která odpovídá common language runtime (CLR) modul načíst v procesu.|  
|[CanUnloadNow – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|Určuje, zda knihovnu, která byla vydána v [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní je stále používáno nebo může být odpojen.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRDebugging` rozhraní pomocí [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
